---
title: "Strange partition errors and using Ubuntu to fix those to install annoying gaming OS"
date: 2017-06-03
forum: Windows
---

### Post by plzhelpminhell on 2017-06-03
Hey, all. I need some help.


I just got a new hard drive for my laptop to replace an old one that went bad. Unfortunately, an operating system I occasionally use for gaming (Windows 7 64-bit) will not install to the laptop (or work, on the one occasion I've succeeded).


Every time I've tried to install Windows 7 (32-bit or 64-bit), it tells me that it can't format any of the partitions on the hard drive and/ or that Windows could not be installed on unallocated space, always giving me error code 0x80070057.


Booting into cmd and using diskpart gives me generic "I/O error"s when I try to format anything.


Windows XP also gives me an error when trying to format either the hard drive or any particular partition.


The one occasion I did get it to install was by booting up into Ubuntu live and using gparted (which always gives me a warning telling me that the device driver believes the block size to be 2048, but Linux thinks it's 512, whatever that means) and gnome-disks to create a new partition table using the msdos option and then did a (quick) format in NTFS.


It took five hours to install, and once it did, everything (including Windows explorer) started failing randomly within two minutes of booting up the computer.


I also briefly tested a Linux installation on the hard drive and installed a bunch of software using apt-get, which all seemed to work fine (in contrast to Windows, which couldn't modify anything on the filesystem without falling apart).


I deleted Ubuntu after a couple hours of use, but I noticed no problems with it.


All BIOS dianogstic tests (memory, hard drive, etc.) pass with flying colors, other than battery, which fails miserably, because the battery is basically dead.


CD/DVD/USB all work fine, and I was ripping DVDs using an Ubuntu USB install for weeks before I got the new hard drive, with no problems.


I can't figure out for the life of me why this is happening. Does anyone have any ideas? Any help you can provide is greatly appreciated.

---

### Post by howefield on 2017-06-04
Thread moved to the "*Windows*" forum.

---

### Post by yancek on 2017-06-04
> always giving me error code 0x80070057.

Did you do an online search for that windows error?  Get lots of hits, the link below is the most detailed of the one I found so you might try it.  Scroll down to the section on gettingthe error during install.

[http://www.fixerrs.com/2014/04/Fix-Error-code-0x80070057.html](http://www.fixerrs.com/2014/04/Fix-Error-code-0x80070057.html)

I'm not sure why you are posting your question on the failure to install two different windows operating systems on an Ubuntu Linux forum?  Have you tried posting at the microsoft support site or some windows forum?

---

