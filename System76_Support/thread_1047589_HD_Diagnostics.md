---
title: "HD Diagnostics"
date: 2009-01-22
forum: System76 Support
---

### Post by cmnorton on 2009-01-22
I have a gazelle ultra. 

I've had three fsck checks today, but have had no unusual shutdowns until after the second fsck.

The second fsck came after I got a BIOS error about time/date changing. I pressed F1 to continue; the fsck said it corrected a problem and the system would reboot. 

The system rebooted. Then, I shifted to boot screen mode (CTRL+ALT+F1), but the screen never updated after printing resuming normal boot. I waited and listened for HD activity, and then I force powered down the system.

The third fsck came after that. I've never had an Ubuntu/Kubuntu system require an fsck on a forced shutdown, but I know that can happen on full running Linux systems.

Are there any HD diags I can run and instructions on how to run them?

Thanks

---

### Post by unutbu on 2009-01-22
[list]
[*]caljohnsmith gives instructions on testing hard drive health using smartctl here:
[http://ubuntuforums.org/showpost.php?p=6575111&postcount=32](http://ubuntuforums.org/showpost.php?p=6575111&postcount=32)

(Note: not all drives recognize S.M.A.R.T. commands, but maybe this will work for you.)
[*]```

sudo tune2fs -l /dev/sda1 | grep state
```
Will tell you if the ext2/ext3 filesystem on /dev/sda1 is clean or unclean, though I'm not sure that is what you are looking for.

[*]If you have a Seagate drive, Seagate provides their own proprietary hard drive diagnostic tool here:
[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)

If you have a drive of a different manufacturer, maybe check their website for similar tools.
[/list]

---

### Post by thomasaaron on 2009-01-22
A forced shutdown can hose a filesystem from time to time, particularly if the HD is writing when the shutdown happens.

My guess (since it is a new computer) is that somehow the fielsystem got borked and fsck isn't able to correct it.

---

### Post by cmnorton on 2009-01-22
Ubuntu 8.10
Gazelle Ultra

Once the time/date got fixed, it stopped doing the fsck. So, it all seems OK, now.

---

