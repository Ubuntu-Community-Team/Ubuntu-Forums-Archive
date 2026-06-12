---
title: "RAID 5 unknown filesystem"
date: 2012-01-11
forum: Server Platforms
---

### Post by bayonetblaha on 2012-01-11
Hello Ubuntu folks. I'm trying to install ubuntu server 11.10 with a software RAID 5 and software RAID 0. The installation goes fine, but I always get this error when I attempt to boot afterwards:

error: unknown filesystem
grub rescue>

These are my partitions:

1.5 TB HDD
	100 GB ext4 mounted as /boot
	400 GB ext4 used as part of RAID0
	1 TB ext4 used as part of RAID5
1.5 TB HDD
	100 GB ext4 used as swap
	400 GB ext4 used as part of RAID0
	1 TB ext4 used as part of RAID5
1 TB HDD
	1 TB ext4 used as part of RAID5
1 TB HDD
	1 TB ext4 used as part of RAID5

RAID 5 - 3 TB
RAID 0 - 800 GB

Any ideas? Can I have multiple RAIDs like that? Could it be the attempt I made to have motherboard RAID that messed something up?

---

### Post by rubylaser on 2012-01-11
I've seen a fair number of people with mdadm issues on 11.10.  Is there some reason, you're not using the [10.04 Long Term Service release alternate install]("http://releases.ubuntu.com/lucid/ubuntu-10.04.3-alternate-i386.iso")?  That would set this up for you during the install, and work fine.

---

