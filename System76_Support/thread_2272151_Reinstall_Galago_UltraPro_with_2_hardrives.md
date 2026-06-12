---
title: "Reinstall Galago UltraPro with 2 hardrives?"
date: 2015-04-04
forum: System76 Support
---

### Post by UberGeekInc on 2015-04-04
Hi.

My Galago UltraPro came with 2 drives with Ubuntu pre-installed.  

I would like to reinstall - but the Ubuntu Desktop installation does not appear to support multiple disks (while the Server version may).  I'd like to use LUKS on LVM (very familiar with LVM, less so with LUKS).  (other distros like openSUSE, Fedora and Arch all support this)

I'd like to know the best way to do this - perhaps how System76 did it?  (pointers to RTFM would be fine)

Jeff

---

### Post by Vladlenin5000 on 2015-04-04
Ubuntu desktop certainly supports such installation. Comparing to server it indeed lacks drivers/firmware for some RAID controllers, not applicable to a System76 Galago UltraPro. 
What complicates things is LVM but since you're very familiar with it, you should have no problem. And LUKS is a drive wide encryption only...

So, what led you into thinking it couldn't be installed? And if you must, you can install server and then add ubuntu-desktop. The end result is the same plus server packages, of course.

---

### Post by UberGeekInc on 2015-04-05
Hey Vladlenin5000.

I didn't say I couldn't install it - just wanted to know how System76 how they did it.

It appears the Desktop edition GUI installer does not handle multiple disks - though setting the disks up via the command line beforehand may work before starting the installer.   I'm anxious about doing it this way as I am not certain to setup a supported method (like setting a crypto file for other LVM partitions to decrypt, from root).

I already tried the Server edition - the disk portion appears exactly the same as Debian's, which I've used previously for similar setups.  The one thing that the Server edition lacks is wifi support - so I'd have to use a usb to ether adaptor and cat 6 cable  (call me lazy!).

Thanks for your comment.

Jeff

---

