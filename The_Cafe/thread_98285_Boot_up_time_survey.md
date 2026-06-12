---
title: "Boot up time survey"
date: 2005-12-02
forum: The Cafe
---

### Post by Paul Casey on 2005-12-02
This is related to thread:
[http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

How long does it take to boot your Ubuntu box?

My new default (boot) install of Ubuntu 5.10 takes 50 seconds to boot on my Shuttle XPC SN85G4.

([http://global.shuttle.com/Product/Barebone/SN85G4%20V3.asp](http://global.shuttle.com/Product/Barebone/SN85G4%20V3.asp))

This time is measured from the moment Grub starts to display of GDM. The Shuttle takes about 15 seconds from when power on thru BIOS test to when Grub loads.  I configured / as an ext3 file system and /home as an XFS file system. And swap is at the beginning of the disk.  (7200 rpm ide disk) Don't know if any of the disk layout affects boot up time.  I DO know that if you configure the entire disk as XFS file system then Lilo boot loader wants to install and then you don't get the nice USplash Ubuntu startup.

Anyway I'm wanting to reduce boot up time.. and will refer to the thread listed above...but in the meantime am curious what others are getting for boot up times.

---

