---
title: "Deleting Software RAID Paritions"
date: 2009-04-29
forum: Server Platforms
---

### Post by CarlosinFL on 2009-04-29
I wanted to install Ubuntu server on a machine that was previously installed with Debian and using software RAID. When I go to try and partition the disk, I see the old /dev/md0 and /dev/md1 listed.

I first remove the 'software raid' listed on /dev/sda and /dev/sdb however I still have /dev/md0 and /dev/md1 listed at the top. When I select them I am given the option to 'remove all data' from RAID and when I select to do so, it moves at 1% per hour. It's crazy slow. I have this problem on any system I try with Debian or Ubuntu installed. Is there a trick of an easy way to remove these old software RAID partitions?

---

### Post by samosamo on 2009-04-29
You want to read up on the "zero superblock" function, post back if you have problems after that

---

