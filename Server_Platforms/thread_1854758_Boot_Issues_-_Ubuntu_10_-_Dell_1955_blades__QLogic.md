---
title: "Boot Issues - Ubuntu 10 - Dell 1955 blades / QLogic HBA / Dell Powervault 660F"
date: 2011-10-05
forum: Server Platforms
---

### Post by rokdevil on 2011-10-05
I've got a 10-blade enclosure with 1955s, an EMC fiber switch and a powervault 660f.  I've installed the first server and have  no issues booting if the 660F is OFF.  If I turn it on after I boot I can see the logical drive of the SAN, although I haven't tried to mount it.
If I power cycle (hard or soft) and leave the 660F on the server craps out on boot, unable to locate the boot partition.  I get a message like this:
alert dev disk by-uuid does not exist

Any ideas?

---

### Post by lcman on 2011-10-05
> **rokdevil said:**
> I've got a 10-blade enclosure with 1955s, an EMC fiber switch and a powervault 660f.  I've installed the first server and have  no issues booting if the 660F is OFF.  If I turn it on after I boot I can see the logical drive of the SAN, although I haven't tried to mount it.
If I power cycle (hard or soft) and leave the 660F on the server craps out on boot, unable to locate the boot partition.  I get a message like this:
alert dev disk by-uuid does not exist

Any ideas?

Looks like a kernel problem. Maybe the kernel hasn't been built with full support for your kind of drives.

I think you need to do a fresh install WITH the SAN turn on and connected. If you've been a redhat user at all, there's a section called Basic storage and Specialized devices when you launch an installation, however, I believe Ubuntu server automatically detects that for you.

So, do a fresh install and see if it gets fixed!

---

### Post by rokdevil on 2011-10-05
Good idea.
I'll let you know how it goes.

---

### Post by rokdevil on 2011-10-05
I did the install with the san on and it detected it no problem.
However, now upon reboot the system never even gets to grub.
My suspicion is that the system is that the system is trying to boot off of the san device.  However, I've sat and waited and haven't gotten any feedback.  System just sits.
When I go to recover a broken disk I choose to mount /dev/sdc1
I then fdisk -l
I get:
Disk: /dev/sdb: ...(this is the san drive)
Device    Boot   Start   End         Blocks   Id   System
/dev/sdb1  *         1   188296  1512481792    7   HPFS/NTFS

Disk: /dev/sdc
Device    Boot   Start   End         Blocks   Id   System
/dev/sdc1            1  8508         blah     83   Linux
/dev/sdc2 blah
/dev/sdc5 blah


Haven't been able to figure out how to get the system to load the SAN device after the SAS card yet.

I just went through a full install again and noticed that grub is using the MBR of sdb, which is the SAN device.
Finally figured it out.
Had to do:
grub-install /dev/sdc

Thanks for your help.

---

