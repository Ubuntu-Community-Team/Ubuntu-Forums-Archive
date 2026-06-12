---
title: "PowerPanel BE fails to read ttyS0 in 12.04 server"
date: 2012-10-03
forum: Server Platforms
---

### Post by jdmcmillian on 2012-10-03
Ubuntu 12.04 server x64
CyberPower Power Panel Business Edition 2.2.1

Does anyone know why PowerPanel fails to talk to the ttys0 serial port in 12.04?  It works fine in 11.10 and 11.04.  And it works well through a virtual box of 11.04 installed inside of host 12.04.  But when installed directly on the 12.04 system, it fails to communicate with the serial port. Was something 'subtly' changed?  Can it be tweaked back?  I really don't like having to run the UPS control program through a virtual box to control the system.  It makes shutting down very dirty.

---

### Post by hasan.akgoz on 2012-10-04
Can you see above command output ?

dmesg | grep tty

---

### Post by jdmcmillian on 2012-10-06
Sorry for the late reply. I've eliminated the virtual machine, here's the output from the command:

Output from server-01
```
root@server-01:/working# dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.334182] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.560728] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.112596] usb 4-2: pl2303 converter now attached to ttyUSB0
root@server-01:/working#
```

PPBE does communicate through a USB to Serial Port adapter, but not through the normal serial port on the real machine with 12.04 installed. 

PPBE appears to be written in java, and the installation includes a loading a JRE into the installation folder along with it. I don't think this is important, but I've included the information in case I'm not thinking of something.

My current line of thinking is that there is another program on server-01 interfering with the serial port in some way.  Is there a way to determine if any other programs are accessing the serial ports?  What are your recommendations and suggestions?

Thanks

---

### Post by jdmcmillian on 2012-10-13
I hate bumping, but its been a week... should I assume no one has any idea on how to test this situation?  Does anyone know why PPBE would work on a serial port (via usb adapter) and not a standard serial port?  yet, ubuntu could handle the serial port if it was passed into a virtual box first?

---

