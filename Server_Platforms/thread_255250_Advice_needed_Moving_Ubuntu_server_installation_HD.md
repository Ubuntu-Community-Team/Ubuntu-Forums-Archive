---
title: "Advice needed: Moving Ubuntu server installation HDD"
date: 2006-09-11
forum: Server Platforms
---

### Post by kwambus on 2006-09-11
Hi,

Pretty new to Ubuntu/Linux servers and I have an issue I need some advice on:

We have a fully working configured Ubuntu (Dapper) server installation I spent lots of hours on getting Postfix/Courier/MySQL configured. However we require that system box to be de-comissioned and I would like in a perfect world to move the existing HDD to another machine as the primary drive.

I have tried this and whilst the HDD is recognised, the boot up sequence gets stuck at the Kernel load up. It then times out to:

ALERT! /dev/hda1 does not exist!

and leaves me at a prompt.

I have booted from the server CD in recovery mode and can actually access the root drive from a shell, I am sure this is a setting somewhere, can somebody point me in the right direction? I really dont want to loose the hours of work I put into the installation :(

Thanks.

---

### Post by ajgreeny on 2006-09-11
Use a live CD with gparted to check that the partition hda1 is correct and does have the linux install on it, and if needed mount the correct partition to change the grub menu.lst file.

This is assuming that you are trying to use grub to boot, and that grub is not finding the partition that the menu.lst file is pointing to.  If that is not the problem, then I'm afraid I can't help you, but I'm sure somebody else will be able to.

---

### Post by kwambus on 2006-09-11
The partition on HDA1 does indeed contain the root directory and is in working order. I would appear that the mount details may have changed in some way? or perhaps the kernel might need re-installing? Not sure but the data is indeed in place, I can access it from the Recovery Mode shell.

---

### Post by kwambus on 2006-09-11
Any ideas from anyone how I can persue this problem?

---

### Post by Frogger on 2006-09-11
Is the livecd seeing the HDD as Hda?  Or do you possibly have it at another location, you could make sure you are on the primary IDE line and jumper the drive as master (vs the cable select you could possibly be running) and try booting lake that.
Next I would try reloading grub (with grub-install) just in case.
Another possiblity is loading the CD kernel and directing grub to boot that kernel.

---

### Post by kwambus on 2006-09-13
Solution to my problem was that CDRom was for some reason on channel 0. I swapped the cable and voila booted up.

Thanks everyone for your input.

---

