---
title: "Upgrading from Trustix to ubuntu"
date: 2008-12-10
forum: Server Platforms
---

### Post by adrianp918 on 2008-12-10
Hello, i currently am going to upgrade to ubuntu from trustix, my question is would i have to format al drive that are on the machine or can i just format the one drive that i plan to install ubuntu on, and keep the other drive as they are with this file system

Linux Native Filesystem (ext3)

there is alot of data on those drives and i dont want to loose it. is this at all poss?

---

### Post by ajgreeny on 2008-12-10
No problem.  If you are using the live CD, boot it to check your hardware is detected and then choose install.  At the partitioning part choose manual and your disks/partitions will be scanned and offered to you for the installation.  Just make sure here that you make the correct choices and don't format or install into the partitions or disks that you want to keep.

As trustix is a linux already installed, the ubuntu installer will probably find it and add it to the grub menu for you, giving you the option to boot to it when and if you need to.  All your data should be safe, as long as you don't format the wrong partitions at installation.

---

### Post by adrianp918 on 2008-12-10
ok Thank you for your help, I will do this and report the end result back, one other question, will I still be able to use this disk in my system with its current file system the one disk storing all my data that is?

---

### Post by ajgreeny on 2008-12-11
If the disk/partition is ext3, vfat or ntfs there will be no problem with using it in ubuntu, trustix nor windows.

---

