---
title: "Ubuntu 14.04 Cannot figure out how to setup LVM + Raid 1 during install."
date: 2014-12-06
forum: Server Platforms
---

### Post by hondaman on 2014-12-06
Can someone please tell me what I'm doing wrong?

I manually added a /boot partition on sda and sdb.  I then used the rest of the disk as a raid 1 type.

I then selected the raid partition and added a physical volume.  Then I used that physical volume to add 3 logical volumes.  One for root, swap and home.

I don't see where or how I can tell the installer that the logical volume I called "root" is actually / though.  When I try and proceed, it says "no root file system defined"

---

### Post by TheFu on 2014-12-07
> **hondaman said:**
> Can someone please tell me what I'm doing wrong?

I manually added a /boot partition on sda and sdb.  I then used the rest of the disk as a raid 1 type.

I then selected the raid partition and added a physical volume.  Then I used that physical volume to add 3 logical volumes.  One for root, swap and home.

I don't see where or how I can tell the installer that the logical volume I called "root" is actually / though.  When I try and proceed, it says "no root file system defined"

When it comes to non-default setups, the Ubuntu installer seems to fight with us. That has been my experience.  I've seen highly complex storage configs created with CentOS installers, but I haven't made the switch over this, yet.  My attempts to get a non-default partitioning and encryption setup out of the installer has always failed. If the defaults where terrible for my needs, it wouldn't matter.

BTW - the type of RAID will be important - software-RAID, Fake-RAID, or HW-RAID with a good controller?

---

### Post by volkswagner on 2014-12-07
Once your Volume Groups and logical volumes are set, you will go back into the partitioner and select your logical volumes and choose "Use as" 
which chooses filesystem type or swap, then you'll see drop down choice for mount point.

[This tutoria]("https://wiki.debian.org/DebianInstaller/SoftwareRaidRoot")l has nice screenshots, it's for Debian, but screens should be the same.

---

