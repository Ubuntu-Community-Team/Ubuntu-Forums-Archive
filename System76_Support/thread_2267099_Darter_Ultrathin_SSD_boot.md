---
title: "Darter Ultrathin SSD boot?"
date: 2015-02-27
forum: System76 Support
---

### Post by e-peter on 2015-02-27
I've just received a Darter Ultrathin.  It has a 500 GB HDD and 256 GB SDD, but the previous owner wiped the OS.  Should it be able to boot from the SSD (setting BIOS options obviously).  During initial install, there was an error when installing the boot loader (wasn't in a position to check the error sorry). 

I have it booting now fine from the HDD, and the OS is also presently mirrored on the SSD.  Before I go mess around and try and reinstall grub, should this work?  Or might I need to make a /boot partition on the HDD?   And how about swap - should I leave that on the HDD?

On a different note, I've never owned a touchscreen laptop; is there anything worth trying or choosing in terms of window manager to make this really useful?  Sure, dragging windows round with my finger is fun, but the tiny tools make this a non-practical use in general.

Thanks!

---

### Post by JeQhdMD on 2015-03-01
I would recommend installing the OS and boot loader on the SSD . . and given the size of the SSD, I would personally put the whole file system on it . . . in other words, the / tree including all user home folders.   Then the HDD could be used for backup and also for excess/large files such as audio and video.  

Re the second question, I'm not a fan of touch screens on real PC's (either desktop or laptop).   Much finer and more consistent response from mouse, trackpad and especially hot-key combos.   Even better/faster than Voice for complex actions.

---

### Post by e-peter on 2015-03-01
I eventually did manually install grub on the SDD and then upgrade (I had installed 14.04), without too much hassle.  I don't know what the original error was, but it all seems OK now.  I'll probably mount the HDD under a backup folder in my home directory.  

Certainly the default tool sizes on windows are way too small for effective finger usage.

---

