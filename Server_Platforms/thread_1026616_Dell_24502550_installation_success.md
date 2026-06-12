---
title: "Dell 2450/2550 installation success"
date: 2008-12-31
forum: Server Platforms
---

### Post by Mark B. on 2008-12-31
Like many others, I had problems installing Ubuntu (and other Linux) on Dell 2450/2550 servers with Perc raid controllers.  Recently I stumbled upon a simple solution.  Last night I did a new install of Ubuntu 8.04.1 on a Dell 2450 in about 20 minutes.

Hardware and materials:  
           Dell 2450, three 36G scsi configured as one raid 0 container.
           External Sony usb CD/DVD drive
           Two (2) copies of Ubuntu 8.04.1 

Procedure:

1. Power on system, and place one CD in each drive (internal CD and external Sony drive).  NOTE: My system will not boot from the USB drive.

2. Proceed through server install. Very early in the process, the kernel is loaded and the screen goes blank. It appears to perform some hardware discovery, and finds the installation disk on the USB drive. The remainder of the install can occur then from the USB disk.  

Notes: 
I have varied the process trying to see what is going on.  I have ejected the internal disk as soon as the kernel loads, and the install proceeds OK.  I have also left the disk in the internal drive, and later on I see the drive light flashing, so it appears to use the disk AFTER loading some material from the USB drive. Either way seems to work. 

Your mileage may vary.
I'm interested in other folks experience with this.
-mark

---

