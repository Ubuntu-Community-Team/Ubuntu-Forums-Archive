---
title: "Xubuntu, GRUB won't install"
date: 2012-12-10
forum: System76 Support
---

### Post by alphaamanitin on 2012-12-10
Trying to wipe the new System76 Pangolin Performance computer I have.  Went to over do the install over option, and it fails to install GRUB on /dev/sda.  Any thoughts?  This is from a USB with the Xubuntu 12.041 LTS via UniversalPenDrive.  I plan on burning a CD-ROM of Xubuntu 12.041 LTS and testing that.  

Any thoughts guys?  Seems really odd.  

AlphaA

---

### Post by alphaamanitin on 2012-12-12
Was able to get it installed via manually settting up the partitions and the like.  Also, could have done it via booting into livecd, mounting my drive to a new mount point etc etc.

AlphaA

---

### Post by samalex on 2012-12-21
Use boot-repair from a Live boot CD.  These instructions describe installing it after installing Windows as a second OS, but either way it just evaluates your system, configures GRUB appropriately, and pushes it to your MBR. You may have some extra boot options if you have partitions that may be bootable, but you can always edit those out later.

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Hope this helps --

---

