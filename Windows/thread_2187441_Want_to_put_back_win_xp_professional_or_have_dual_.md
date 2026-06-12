---
title: "Want to put back win xp professional or have dual boot"
date: 2013-11-12
forum: Windows
---

### Post by matt.barnett on 2013-11-12
The Windows Xp disk i have is "only for distribution with a new pc"

the machine has an xp license.

It will only install if hdd is formatted

using gparted I managed to remove linux partitions and install NTFS partition but it still thinks Linux is already there and comes up with grub error

---

### Post by Bucky Ball on 2013-11-12
*Thread moved to **Other OS/Distro Support**.*

Last I knew Windows you can format the partitions when you install Windows. No need to set up partitions first (done it with XP too many times in the past). You need to rewrite the MBR which I think you can do with Windows recovery. Hopefully someone who knows can help you out with this.

From memory, when you boot he Windows install CD, a little bar comes up along the bottom at some point asking if you want to do a Windows recovery. Hit y or whatever you need to and see what options you get.

---

### Post by BBQdave on 2013-11-13
Not to be a bummer, but you may want to consider the age of your hardware, and the hassle of a Windows XP install - of a system that will be unsupported soon.

What ever is needed of your system, you may want to consider an up to date Linux distro - again, if that will meet your needs. Best to run a supported system :)

---

### Post by lykwydchykyn on 2013-11-14
Seems like in ages past I ran into this problem, and the solution was to completely blank the disk using something like darik's boot-and-nuke or the "dd" command from a linux boot cd.

---

### Post by oldfred on 2013-11-14
Is NTFS partition primary or sda1 thru sda4 and does it have boot flag? Windows only works with primary partitions with the boot flag.

---

