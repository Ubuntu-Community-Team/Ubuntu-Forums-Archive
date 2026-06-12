---
title: "installation stuck"
date: 2012-01-26
forum: Ubuntu Studio
---

### Post by Terrywho on 2012-01-26
Fresh install of UbuntuStudio 11.10, burned the iso and checked the md5sum ok,
put in the DVD to change from Fedora 15, it detected the hardware ok (Dell desktop), and partitioned the disks ok, then in the middle of installing the base system a message pops up to insert the UbuntuStudio 11.10 CD in the drive and hit continue.  Well, it already has the UbuntuStudio 11.10 in the drive, I cannot eject the dvd, hitting continue just pops the same message up again.  
Any suggestions would be appreciated.
Thank You.

---

### Post by jejeman on 2012-01-27
Try again. Try multiple times to press ok when question pops.
Hope you read release notes for 11.10.

---

### Post by Terrywho on 2012-01-27
Yes, I tried re-installing it several times and it always failed in the same place, about 77% of the way into the base system install just after config APT sources.
Re-installing also multiplied the partitions each time.  

I was successful installing xubuntu 11.10 alternative, and try to build ubuntustudio from that.  Although doing an sudo apt-get install linux-rt did not find anything?

I was following the web page on other methods of installing ubuntustudio.

any suggestions?

---

### Post by varunendra on 2012-01-28
Try writing the disc at minimum possible speed using the same drive which you have to use for reading it. Or, try a live USB. This thread maybe interesting to you:
[http://ubuntuforums.org/showthread.php?t=1813055](http://ubuntuforums.org/showthread.php?t=1813055) (post #5 onwards)

---

### Post by jejeman on 2012-01-28
> **Terrywho said:**
> I was successful installing xubuntu 11.10 alternative, and try to build ubuntustudio from that.  Although doing an sudo apt-get install linux-rt did not find anything?

I was following the web page on other methods of installing ubuntustudio.

any suggestions?Rt kernel is there just for 10.04 32bit.
Just install other meta packages. If jack gives you bad performance, try lowlatency kernel from Abogani ppa.

---

### Post by Terrywho on 2012-01-29
Success, I was able to install ubuntustudio 11.10 using the same DVD as before but on a newer system.  I think the original Dell dimension 9100 is getting old, bios A01 circa 2005. Thank you all for your help.

---

### Post by linuxmatt7 on 2012-05-06
Go ahead turn off your computer and restart install. If it continues just redownload and reburn the CD/DVD image.

---

