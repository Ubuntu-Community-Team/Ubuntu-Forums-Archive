---
title: "ubuntu/wubi and windows 10"
date: 2015-08-16
forum: Ubuntu, Linux and OS Chat
---

### Post by ricktoday1 on 2015-08-16
I have been running 14.04.3 alongside Windows 7, which came from upgrading a 12.04 wubi install.  (I know, but I was new to this at the time and didn't have a dvd burner).  Anyway, with my newer laptop and a dvd burner, I downloaded 14.04.3 ISO and burned an install disk, in preparation for the windows 10 upgrade.  When it was finished to my amazement, ubuntu was still intact and runs fine.  The only thing I don't like is that Win 10 seems to have inserted itself into the grub loader and now I get a splash screen asking which operating system I would like to boot, but so far I haven't had any problems with ubuntu, beyond drivers.  Just thought I 'd pass this along for the the few greenies like me, that are still running a wubi version.  

I will probably use the install disk anyway, because I'm hoping it will fix my nvidia driver problem with an external monitor.  No nvidia driver I've been able to try with the wubi version works on this Dell 64 bit laptop without locking up on the external monitor.

---

### Post by kayodu on 2015-09-19
Dear Ricktoday1,

I was deliberating on upgrading my Windows 7 in which, like you, I have 12.04 wubi installed and upgraded to 14.04.  I am reluctant to change to Dual Boot as I would lose the advantage of easy access to my files in Windows neither do I want to run Ubuntu from a Virtual machine in Windows.

I am encouraged by your experience to give it a try after backing up my files of course.

Thanks.

Kayode



> **ricktoday1 said:**
> I have been running 14.04.3 alongside Windows 7, which came from upgrading a 12.04 wubi install.  (I know, but I was new to this at the time and didn't have a dvd burner).  Anyway, with my newer laptop and a dvd burner, I downloaded 14.04.3 ISO and burned an install disk, in preparation for the windows 10 upgrade.  When it was finished to my amazement, ubuntu was still intact and runs fine.  The only thing I don't like is that Win 10 seems to have inserted itself into the grub loader and now I get a splash screen asking which operating system I would like to boot, but so far I haven't had any problems with ubuntu, beyond drivers.  Just thought I 'd pass this along for the the few greenies like me, that are still running a wubi version.  

I will probably use the install disk anyway, because I'm hoping it will fix my nvidia driver problem with an external monitor.  No nvidia driver I've been able to try with the wubi version works on this Dell 64 bit laptop without locking up on the external monitor.

---

### Post by oldfred on 2015-09-19
Wubi is not supported anymore, so you guys are on your own.
 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

All versions of Ubuntu have the NTFS driver to read & write NTFS partitions. 
Just that with Windows 8 & later, Windows uses all the time hibernation to speed booting called fast start up and that must be off to dual boot.

---

