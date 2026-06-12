---
title: "no reaction on usb devices"
date: 2009-08-11
forum: Server Platforms
---

### Post by Liam Larks on 2009-08-11
Hi at all,
I am new to Ubuntu, and started setting up a little homeserver with 8.04.
My probem is, the server does not gecognize any usb device plugged in at one of the two USB 1.1 Ports.
There is no message in the udev monitor,
and also just the two internal disks in blkid.
I' m using a Pentium 3 at app. 800Mhz and an Asus CUV4X-M Mainboard (USB onboard)

Thanks in advance;)

Liam

---

### Post by JHan816 on 2009-08-12
I am new to this too and have a 8.04 server on an old Compaq Presario with the older 1.1 ports.
 Have you tried the command:
lsusb -v 
This will give you a detailed list of the ports. Maybe something will show.
Again, I am new to this too and I hope this helps.
 
Also check USB settings in bios to see if enabled.
 
Sincerely,
John

---

