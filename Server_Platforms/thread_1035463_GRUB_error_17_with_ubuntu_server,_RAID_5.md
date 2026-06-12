---
title: "GRUB error 17 with ubuntu server, RAID 5"
date: 2009-01-09
forum: Server Platforms
---

### Post by DrIdiot on 2009-01-09
Hi,

I set up Ubuntu server 8.10 on a machine and used RAID-1 to mirror two drives.  Everything worked fine, everything installed, I could boot, etc.

Now, I set up the server with four drives, with RAID-5.  The install completed successfully, but when trying to boot, I got an error from GRUB, GRUB error 17.

I looked online and most of the solutions seem to say that it has to do with BIOS configuration (they tell you not to set your BIOS configuration to RAID because Ubuntu is using software RAID).  However, my BIOS config is not set to RAID, and I didn't change the BIOS configs between the two installs, so this isn't my problem.

Also, I booted to an Ubuntu LiveCD and checked with parted; my swap partitions do not have boot flags, so that is not the problem.

I noticed that there was some sort of warning during installation about /dev/md0 not being up to date so a restart was necessary before doing something.  However, I remember getting this both times, so I didn't think it was the issue.  But maybe it is?

Does anyone have any light to shed on this situation?

Thanks.

---

### Post by DrIdiot on 2009-01-09
The issue has been resolved.  You can't boot to a RAID-5 partition.

---

### Post by Cracauer on 2009-01-09
Strictly speaking:

/boot has to be plain or raid-1

/ (root) can be raid-5 but requires that the appropriate raid modules are compiled into the kernel or are in the ramdisk.

---

