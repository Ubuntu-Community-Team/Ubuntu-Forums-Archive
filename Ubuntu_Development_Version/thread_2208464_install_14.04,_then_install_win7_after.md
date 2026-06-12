---
title: "install 14.04, then install win7 after?"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-28
that will work ok?

I only partitioned the front half of the drive for ubuntu, seperate home, etc.... Left the remaining for windows.

How much space do you leave for / the os?

---

### Post by su:bhatta on 2014-02-28
Yes, that will work. 
I have done that. 

All you got to do is get yourself a program to get the Ubuntu entry to choose when system starts up.  
EasyBCD  is a program which you can install in Windows to make it configure the BCD/BOOTMGR bootloader for Windows Vista, Windows 7. 

If you want to only load the Windows7 then typically 15-20Gb space is enough. I have my Windows 8 in a 25Gb partition and nearly 5Gb is unused. Safely a 40-50 Gb partition for Windows7 should be sufficient.

Also, follow this thread it has some information : [http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

---

### Post by sdowney717 on 2014-02-28
right, super grub rescue fixes boot issues.

I allowed 15gb for the OS, which is too much maybe?
drive is 80gb total.

what I have left is 28gb for windows.
Plan is to use it for watching tv and videos.
With win7 and WMC, maybe the thing can run as an extender or appliance.

Would like to watch the live TV on it.

---

### Post by su:bhatta on 2014-02-28
15 GB should be sufficient for Ubuntu 14.04 if you are not planning on loading a lot of extra programs or big games (Never load games, no idea how much those shooters and all eat up)

My Ubuntu Drive is '/'=24Gb, that too I install Ubuntu Studio (2.6Gb iso) + I install KDE on top of it and loads of audio programs and all. 
Still I have 8-9 Gb space left.
Problem becomes if & when I download big videos, then it gets tad crunchy :) 

28Gb for Win7 for watching video's & TV is a playground. 
I just keep  Win8 with Office 2013 there, for just  in case something pops up, which has bever been the case for nearly a year.

---

### Post by sdowney717 on 2014-02-28
15gb was just for the OS itself, /home in another partition 35gb.

I never know but maybe 10gb would have been better for the os files.

---

