---
title: "Best software RAID setup for two physicall HDD?"
date: 2008-05-21
forum: Server Platforms
---

### Post by carfield on 2008-05-21
I have 2 HDD with 500GB, but currently my usage is about 50GB only, Just wonder what is the best software RAID setup which provide best performance and good enough data protection? Just RAID 1 with 2 partitions in 2 HDD?  RAID 1+0 with 4 partitions in 2 HDD? or RAID 0 2 partitions in 2 HDD, then have another partition and run custom rsync back program from time to time?

---

### Post by barichardson5727 on 2008-05-21
The most optimal configuration you can get with 2 hard disks that still allows fault tolerance is raid 1. While you can technically still configure nested raid levels across just 2 disks it will only add overhead and increase complexity if there is a failure that you need to recover from, since you will have 2 logical disks failed when only a single physical disk has failed. You would not see any benefit from nested raid levels unless you had 4 or more physical disks with your configuration. 

In the end though, raid should never be considered a backup solution. Backups should always be stored on a device that is physically separated from the server that is being backed up.

---

### Post by carfield on 2008-05-23
Great, thanks a lot!

---

### Post by samosamo on 2008-05-23
i get what you are asking, and this is what i suggest:

10GB / /dev/md0 RAID1 (mirror)
50GB /home /dev/md1 RAID1 (mirror)
439GB /data /dev/md2 RAID0 (stripe)
1GB swap RAID1 (mirror)

that gives you a failsafe system with 878GB for /data, you may want more/less for /home thats up to you.

---

