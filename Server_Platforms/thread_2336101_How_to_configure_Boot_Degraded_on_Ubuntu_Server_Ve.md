---
title: "How to configure Boot Degraded on Ubuntu Server Version 16.04"
date: 2016-09-04
forum: Server Platforms
---

### Post by leonv122 on 2016-09-04
Greetings,

I recently built my first 16.04 server.  It has 2 1TB drives in a RAID 1 for /, Boot, Swap, and Primary Data Storage.  
The boot partitions on both drives is marked as bootable.

It has another RAID 1 of 1TB drives for archive data storage.  

Disconnecting any one drive prevents successful boot and drops to initramfs.

Running dpkg-reconfigure mdadm  does not ask about boot degraded.  I have tried suggestions on [http://askubuntu.com/questions/789953/how-to-enable-degraded-raid1-boot-in-16-04lts](http://askubuntu.com/questions/789953/how-to-enable-degraded-raid1-boot-in-16-04lts) without success.
I'm hoping someone can assist with setting up both raids to boot degraded as neither RAID will boot but drops into initramfs.  

Thanks in advance,
Leon

Additional detail in case it matters:
```
/proc/mdstat:
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sdc3[2] sda3[0](F)
      976320 blocks super 1.2 [2/1] [_U]


md1 : active raid1 sdc2[2] sda2[0](F)
      29280256 blocks super 1.2 [2/1] [_U]


md0 : active raid1 sdc1[2] sda1[0](F)
      9756672 blocks super 1.2 [2/1] [_U]


md3 : active raid1 sdc5[1] sda5[0](F)
      936590336 blocks super 1.2 [2/1] [_U]
      bitmap: 6/7 pages [24KB], 65536KB chunk


md4 : active raid1 sdd1[1] sdb1[0](F)
      976630464 blocks super 1.2 [2/1] [_U]
      bitmap: 4/8 pages [16KB], 65536KB chunk
/etc/fstab:
UUID=a0aa100c-eee2-4667-abc2-73329ae868d9 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md2 during installation
UUID=0915dab4-f031-4241-bba8-66a0cf6a8815 /boot           ext4    defaults        0       2
# /data was on /dev/md3 during installation
UUID=02cfcaa7-e17d-4466-b87a-9a7aeff1e175 /data           ext4    defaults        0       2
# swap was on /dev/md0 during installation
UUID=bd3c42ed-ab0b-4a1e-8828-5e00a28ffe67 none            swap    sw              0       0
/dev/md4 /data/archive   auto    defaults        0       0
```

---

### Post by dom134 on 2016-09-18
Hello there, I have the same issue; a boot partition on raid 1 over 4 disks and then raid 5 for the remainder.  I get the impression that degraded raid no longer seems to work in Ubuntu.  Is this really the case?

---

