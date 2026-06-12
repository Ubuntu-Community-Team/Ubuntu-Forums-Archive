---
title: "Install Ubuntu 9.04 server in a IBM xSeries server"
date: 2009-05-06
forum: Server Platforms
---

### Post by ingtorresurina on 2009-05-06
installed ubuntu on an IBM xSeries 230 server with two SCSI disks ibm 36g each PENTIUNIII 1.2G processor and 1G RAM and installed the ubuntu 9.04 server and I do not post to any problems during installation, I recognized the HD scsi and formatted smoothly at the time of completion of installation and subsequent reboot, I get the following message

Starting up ...
[0,920000] ...MP-BIOS Bug: 8254 timer not connected to IO-APIC
Loading plesae wait
gave up waiting for root device.Common problems
-Boot args(cat /proc/cmdline)
-check root delay=(dis the system waiting enough)
-check root=(did the system wait for the right device?)
-mising modules (cat /proc/modules ; ls /dev)
alert /dev/sda7 does not exist. droppin to a shell!
 busy boy v1.10.2 (ubuntu 1:1.10.2-2ubuntu7)
built-in shell(ash)
enter "help" for a list of built-in commands
(initramfs)_


and not the linux boot, if not the busy boy. 
 may or may not fix you, and how can fix.

---

### Post by ZizzerZuz on 2009-08-11
From this page, click way up there on top left [Ubuntu Forums]("http://ubuntuforums.org/index.php")  	> [The Ubuntu Forum Community]("http://ubuntuforums.org/forumdisplay.php?f=130")   	> [Main Support Categories]("http://ubuntuforums.org/forumdisplay.php?f=327")   	> [[COLOR=Red]**Server Platforms**[/COLOR]  ]("http://ubuntuforums.org/forumdisplay.php?f=339")

Click on that Server Platform part, then on the next page on right the right hand side below the page count and next buttons, click on search this forum for  IO-APIC.

Fixed my problems loading an IBM 220 just a few days ago.  That and removing the PCI SCSI adapter.  Now, if only I could make that work too.

---

