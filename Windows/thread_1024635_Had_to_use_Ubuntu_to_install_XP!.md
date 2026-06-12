---
title: "Had to use Ubuntu to install XP!"
date: 2008-12-29
forum: Windows
---

### Post by tribal_guy4 on 2008-12-29
I am making HP t5700 thin client into an embedded computer for frequent movement about the house, and was trying to boot the computer from either a 4GB compact flash card or an 8GB seagate microdrive.  Both would recognize and format in the first part of the XP setup, but would not be seen as a valid boot device.  After much googling, I found that XP's bootloader will not work from a removable device for some reason (anti-piracy).  Certain CF drives have the ability to be switched to a fixed device with a utility from the manufacturer, however mine were not one of the lucky few.  I ended up trying out a few different linux distributions, and they all would boot without problems.  I decided that there might be a possibility that using GRUB instead of the XP bootloader might bypass the disk type check.  

What I did was to put the microdrive as primary master, and use a USB CD drive to run the XP setup disk.  I ran the setup up until the point where it rebooted.  When it reboots, swap to an Ubuntu live cd and let it boot to the installer.  Install as normal until the partition screen, then resize the windows partition to allow enough room for the Ubuntu installation.  After this, let the setup finish as normal, remove CD and replace it with the XP install CD.  When the computer reboots, it should bring up the GRUB screen with the XP option on it.  Choose it, and the second part of the XP installation should begin.  Let the setup complete as normal, and you will have a working XP install with Ubuntu as a bonus.  At this point you can boot into Ubuntu and change the GRUB menu to what you want to boot by default.  I thought this might be helpful for others, since I have found no other ways around this problem.

---

