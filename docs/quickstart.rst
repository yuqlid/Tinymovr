*****************
From Zero to Spin
*****************

Preparation
###########

If you are using a Tinymovr Dev Kit, please ensure you have completed :ref:`connecting-data` and :ref:`connecting-power`.

If you are using a Tinymovr board in your own setup, please go through the :ref:`hardware-setup-guide`.

Before proceeding to the next steps, ensure your Tinymovr is powered up.

Installing and Launching Studio
###############################

Tinymovr can be installed simply using pip. Python 3.6 or greater is required.

.. code-block:: console

    pip3 install tinymovr
    tinymovr

You should now be looking at the Tinymovr Studio IPython interface.

Installing on Raspberry Pi
##########################

Installation on Raspberry Pi requires a few additional steps.

.. code-block:: console

    sudo apt update
    sudo apt install python3-pip python3-numpy libopenjp2-7 libtiff5
    pip3 install tinymovr

You may also need to append a directory to your PATH variable:

.. code-block:: console

    echo 'export PATH="/home/pi/.local/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

Now you should be able to run Tinymovr Studio:

.. code-block:: console

    tinymovr

Checking Functionality and Calibrating
######################################

.. code-block:: python

    tm1.device_info

IPython should display an array of device-related information.

If you are using a Tinymovr Dev Kit, the motor and encoder should have been already calibrated. If you have your own setup, or if you experience problems with prior calibration, you'll need to go through the following brief calibration procedure.

.. note::
   After issuing the command below, the motor will spin. Ensure the rotor is free of obstructions or loads.

.. code-block:: python

    tm1.calibrate()

Follow the on-screen prompts. The motor will produce an audible beep and rotate in one direction.
Your Tinymovr is now ready for operation. You can view information about the attached motor as follows:

.. code-block:: python

    tm1.motor_config

This will reveal identified motor parameters, namely: phase resistance, phase inductance, number of pole pairs and encoder ticks.

Testing Position Control Mode
#############################

.. note::
   After issuing the command below, the motor will hold position and may spin.

.. code-block:: python

    tm1.position_control()

The motor should now be actively holding it's position. Try moving it by hand and you should feel resistance.

Now try to command a new position:

.. code-block:: python

    tm1.set_pos_setpoint(0)
    tm1.set_pos_setpoint(8000)

The motor should jump to the commanded positions.
