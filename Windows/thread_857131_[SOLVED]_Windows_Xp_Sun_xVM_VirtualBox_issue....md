---
title: "[SOLVED] Windows Xp: Sun xVM VirtualBox issue..."
date: 2008-07-12
forum: Windows
---

### Post by maconga on 2008-07-12
I am on my Windows Xp machine, I installed Sun xVM VirtualBox (1.6.2)...
selected the OS, and the ISO image, i boot the VM and i get a "FATAL: No bootable medium found! System Halted."...
I am trying to run Ubuntu (Don't want to dual boot or use Wubi)


Downloaded the Ubuntu 8.04.1 ISO, Opened Sun xVM VirtualBox, Named the OS Ubuntu 8.04.1, selected Ubuntu, hit next, gave it 256 mb RAM, created new .vdi (dynamic expanding image) hit next, finished... 
Selected the Ubuntu 8.04.1, went into settings, CD/DVD, checked the Mount CD/DVD, selected the ISO image, C:\Documents and Settings\John Doe\My Documents\Ubuntu8.04.1 (yes it is a .iso), clicked Okay, booted, and i get the "FATAL: No bootable medium found! System Halted."

I used this program in Ubuntu (3 months ago) to have a Windows install, and it worked with no problem...

Am i doing something wrong?

---

### Post by TransitMan on 2008-07-14
Double check the md5checksum of the .iso
It sounds like either a bad burn or bad download giving the problems. Do the above and also, if it is a LiveCD, boot into it and have it check the disc before going any further on booting up.

---

### Post by K.Mandla on 2008-07-14
Moved to Windows Discussions.

---

### Post by maconga on 2008-07-16
well... that was weird.... i reselected the ISO image, and it loads...

SOLVED

---

