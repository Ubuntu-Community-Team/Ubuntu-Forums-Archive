---
title: "Hamlet solar BT GPS HOWTO (Ubuntu 12.04 LTS)"
date: 2013-08-27
forum: Tutorials
---

### Post by geppetto on 2013-08-27
This is a short howto that covers the installation of the Hamlet(TM) bluetooth gps device equipped with solar cells on Ubuntu 12.04 LTS. It is an extremely inexpensive device useful to non-professional users, easely found on webstores for about 20 Euros. Surprisingly, I did not find a similar guide in the web. So here is the guide.

To complete the configuration, you need to know how to couple a Bluetooth device, how to install packages, how to use the terminal, and how to edit a text file; your computer must have a built-in bluetooth device, or you can attach a bluetooth dongle to a USB port of your PC. Read the GPS device manual to understand the meaning of led signals and the usage of the button.

The first step consists in associating the GPS device with your computer.

[FONT=Arial Black]Coupling the device
[/FONT]
Coupling (aka associating) is done the usual way: start by pushing the button on the GPS device until the blue led starts flashing rapidly, next select the bluetooth symbol in the upper band on the PC screen, and add a new device. Select the pin 0000 in the "Pin options" menu in the device discovery window.

[FONT=arial black]Setting up communication[/FONT]

The next step consists of discovering how to access the GPS device. First find the bluetooth address:

```

# gksudo hcitool scan
Scanning ...
    00:11:22:33:44:55    HBTSOL

```

Annotate the number you read instead of 00:11:22:33:44:55, that corresponds to the GPS device address, and replace it in the following command:

```

# sudo sdptool record 00:11:22:33:44:55
Service Name: SPP slave
Service RecHandle: 0x10000
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1

```

You need to interrupt the command with a ctrl-C. The important info here is the channel number, which should be 1.

Now edit the file /etc/bluetooth/rfcomm.conf adding the following lines:

```

rfcomm0 {
    bind yes;
    device 00:11:22:33:44:55;
    channel    1;
    comment "Hamlet GPS receiver";
}

```

In case you have another rfcomm0 defined, use rfcomm1.

[FONT=Arial Black]
Install GPS software
[/FONT]
Now you need to install some software: in a terminal type:

```

#sudo apt-get install gpsd gpsd-clients marble

```

and properly configure gpsd

```

#sudo dpkg-reconfigure gpsd

```

Reply to the dialog as follows:

[LIST=1]
[*] Start gps automatically at boot
[*] Automatically connection to the device
[*] set /dev/rfcomm0 (or the rfcomm in the rfcomm.conf) as theGPS device
[*] no options
[*] leave the socket to its default value
[/LIST]

[FONT=Arial Black]
Test
[/FONT]

Type and check:
```

# sudo rfcomm -a
rfcomm0: 00:11:22:33:44:55 channel 1 ...

```
This means that the connection with the GPS device is operational. Now place the GPS receiver close to a window and wait for the red led to blink slowly. Type:
```

# cgps

```
The output after the command is a full screen showing longitude, latitude etc. Success!!! :D

When your PC is correctly configured, to use your GPS device you simply need to switch it on and place it in a suitable position. Start a GPS application on your pc (like marble) and configure it for reading the current position from gpsd.

---

### Post by Bucky Ball on 2013-08-27
*Thread moved to **Tutorials**.*

Nice. Of more use here.

---

