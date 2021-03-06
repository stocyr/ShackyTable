ShakyTable
===========

![ShakyTable Screenshot](screenshot.png)

Embedded android school project with BeagleBoneBlack and BFHCape. Connects to the I2C motion sensor LIS302DL and moves a graphical ball on th edisplay according to the x and y acceleration values.

## Platform

This android app was developed for the Bagle Bone Black microcontroller system running an Android OS.
It also assumes the BBB-BFH-Cape to be mounted on top of the Beagle Bone Black.


## Purpose

The purpose of this application is to connect to the I2C motion sensor LIS302DL and read the acceleration values. Then move a graphical ball on the display of the BFH Cape with a simple physics engine.


## Installation

The android installation package *ShakyTable.apk* has to be installed on the target and the app *ShakyTable* then has to be launched.

-----------------------

## Execution

The app starts in fullscreen, so no space is being wasted for useless app info bars and other stuff :).

After launching, the app automatically connects to the I2C driver on bus 3 and connects to the motion sensor on address 0x1c. Then it reads the x and y acceleration values with a sample rate of approximately 50Hz.

On the display, a ball can be moved by tilting the BeagleBoneBlack towards the desired direction. The acceleration measured by the motion sensor influences the ball velocity which then is used to update the balls position. If it touches one of the four edges, it bounces back with an inverted velocity.

To increase the realistic feel, the velocity is constantly slightly lowered by a small friction value (~ factor 0.995). Also the ball doesn't conserve the whole velocity after bouncing off an edge (just 80%).

## Usage

The four LEDs indicate the balls velocity magnitude (in a logarithmic manner).
The four buttons can be used to change the balls mass. Button T1 is the lowest mass and button T4 the highest.
If all four buttons are pressed, the current sensor motion value is being used to calibrate the device to an even surface. So to calibrate, place the BBB on an even surfave and press all four buttons.