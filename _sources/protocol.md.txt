# Protocol

The control protocol for the Vibratissimo allows the user to:

- Set a pattern/mode
- Control motor speed (when using motor control pattern)
- Retreive the temperature of the device

# Mode Selection

Mode selection is send via writes to the mode selection
characteristic. It is a 2 byte value, though it is currently unknown
what the second byte represents.

Value of the first byte:

- 0x01: Turn device on 
- 0x02: Play pattern that ramps up and down
- 0x03: Put device into "motor control" mode

Sending anything higher than 0x03 will cause the device to stop
working until the host disconnects and reconnects

# Motor Control

If the device is put into "motor control" mode, it can be controlled
via writes to the Motor Speed Control characteristic. It is a 2 byte
value, though it is currently unknown what the second byte represents.

Value of the first byte is 0x00-0xff, with 0x00 turning motor off, and
0xff setting motor full on.

# Temperature

Temperature is retreived via a read from the Temperature
characteristic. It is a 2 byte value, though it is currently unknown
what the second byte represents.

Value of the first byte is temperature, with lower being higher.
