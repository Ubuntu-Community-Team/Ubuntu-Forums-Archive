---
title: "[SOLVED] Installing Windows 95...need help."
date: 2008-12-06
forum: Virtualisation
---

### Post by DOS4dinner on 2008-12-06
Is there a way to install Windows 95 in VirtualBox? I have the original floppies and the original CD, but I don't have a floppy drive. Is there a magic floppy boot disk image file somewhere that would install allow me to install it?

I tried freeDOS, but that can't boot 95.

**EDIT:** Found magic boot disk. In case someones else needs it:
Mount the iso of the Windows 95 disk in Virtualbox.
Download [the patch.]("http://www.bootdisk.com/readme.htm#thepatch")
Download the 95 floppy bootdisk image from [here]("http://www.allbootdisks.com/download/95.html")
Use winimage (A windows floppy program that works in Wine) to add The Patch to the 95b bootdisk.
Mount the bootdisk.
Boot off the bootdisk and run the mount cd iso. 

I haven't tried installing yet, but it should work.

---

