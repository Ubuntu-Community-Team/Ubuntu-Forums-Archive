---
title: "Virtualbox - Gusty server error"
date: 2007-12-08
forum: Virtualisation
---

### Post by wormser on 2007-12-08
I am able to install Gusty server but when I reboot I get the following error:

> Starting up ...
PANIC: CPU too old for this kernel.

I am running a Pentium M 1.86.  It's not that old.

I found a solution in this [thread]("http://ubuntuforums.org/showthread.php?p=3417329#post3417329").

> load feisty install, press alt+f2
mkdir /mnt/hd
mount -t ext3 -o rw /dev/sda1 /mnt/drive
chroot /mnt/drive
apt-get install linux-image-2.6.20-15-generic
apt-get remove linux-image-2.6.20-15-server


I am unable to mount with the server cd.  So, I booted with the desktop cd and was able to mount.  When I run the first apt-get command it asks to insert the server CD.  Virtualbox will not let me change the iso in CD settings since it is booted.  I then tried doing the same from the server CD skipping mounting because it won't.  I get the same error to insert the server CD and the server CD is mounted.  Any ideas on getting Gusty server installed in Virtualbox?  I am installing server on Virtualbox just for learning.

---

