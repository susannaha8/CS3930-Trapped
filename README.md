
# Creative Embedded Systems: Interactive Devices

For our module 1 installation, we used an ESP32 TTGO display, a joystick, and a button to create our own interactive designs. I chose to use PyGame, a python library, to create a visual display that responds to various inputs from my hardware device. Click here for artistic documentation:


## Setting up the Hardware

This project consists of a breadboard, 7 wires, and three main pieces of hardware: an ESP32, a joystick, and a button. Plug the pins of the hardware into the breadboard, and connected them further with wires: connect the joystick to the ESP32 with one wire to Ground, one to 3V, and the other three to pins 25, 26, and 27 for X, Y, and Z motion; connect the button with one wire to Ground, and the other to pin 13 for digital input. The ESP32 is powered via a USBC cable.


## Flashing Code to the ESP32

After setting up our hardware, flash the code found in `src/main.cpp` to your ESP32. This sets up recieving serial input from the joystick and the button. In the code, change the pin numbers if you used different GPIO pins when setting up the hardware. You can either write this code in the Arduino application or through the VSCode IDE PlatformIO. Select the port, and set the baudrate to match whatever you value you put in your `src/main.cpp` code (ex. `Serial.begin(115200);`.) To set the baudrate in PlatformIO, in `platformio.ini`, add the line `monitor_speed = 115200` where 115200 is the baudrate. 

To check that you are recieving serial input, open the Serial Moniter. As you move the joystick and press the button, you should watch the values being printed out change.

## Reading Serial Input

Once you confirm you are recieving serial input, you need to retrieve that input so you can parse it. This is done in `reader.py`. First install the python module serial with `pip install pyserial`. Use the line `ser = serial.Serial('/dev/cu.usbserial-546F1153241', 115200)` to tell serial the port and baudrate, and `str(ser.readline().strip(), 'ascii')` returns a string of the serial input you are recieving from your hardware. This line is in an infinite while loop, so you are continuously recieving lines of input. From there, you can use those values as variables that change color, or position, or any other features of your game.


## Creating My Display with PyGame




