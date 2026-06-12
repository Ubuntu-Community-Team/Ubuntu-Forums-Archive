---
title: "Unable to install Windows 7 on Toshiba Sat Pro"
date: 2014-03-09
forum: Windows
---

### Post by stephen30 on 2014-03-09
I am currently running ubuntu but require to boot windows 7 only my device as well. I have tried to do this through my usb. I have formatted it to NTFS and labled as a boot flag with GParted. Then I have installed the iso file onto the stick using UNetbootin built 494. This all runs well but the BIOS does not read the USB device. I have also installed this iso onto a DVD and again does not recognize the device. My BIOS recognises the USB when installing other linux distributions but not with windows installed. I have also checked the copy of windows 7 with virtualbox and runs perfectly. 

Does any one know how I could install this on my PC and get my BIOS to recognise the USB with Windows 7 on it.

---

### Post by PondPuppy on 2014-03-09
Stephen30, I'm curious about your hardware -- in particular, is it likely to have UEFI installed? (I think, from what user oldfred mentioned on another thread, that hardware newer than about 2011 could be UEFI-enabled.)

---

### Post by newbie2244 on 2014-03-10
Go to BIOS, f10 on my HP Pavilion, and change the boot order. I have Insyde BIOS. Make the usb stick first on the boot order list, or above the Ubuntu Linux Boot location. Insert the stick before you start the system.

---

