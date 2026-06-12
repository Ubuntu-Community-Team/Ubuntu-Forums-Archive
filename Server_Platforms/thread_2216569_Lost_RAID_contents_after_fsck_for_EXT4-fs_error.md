---
title: "Lost RAID contents after fsck for EXT4-fs error"
date: 2014-04-12
forum: Server Platforms
---

### Post by larzeb on 2014-04-12
I am running Ubuntu 12.04 desktop. I created a RAID5 array using mdadm. Suddenly I got a 'EXT4-fs (md0): Remounting filesystem read-only' message and could not use the raid contents.

I booted up with /forcefsck and used the automated recovery. It looked like it worked. When I logged onto the system after that, there were no mount points so I re-created them. However they are empty!

But the detail display for the array shows that it is 13% utilized! How can this be? Have I lost the data?

If I have, I have backup. How do I clear out the contents of the array before restoring the data? 

I would appreciate any advice. Thanks Lars

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        52G  8.6G   40G  18% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           402M  1.2M  401M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  144K  2.0G   1% /run/shm
/dev/sdd1       2.7T  950G  1.7T  37% /media/sysback
/dev/md0        9.1T  1.1T  7.6T  13% /mnt/data



```

```
/dev/md0:
        Version : 1.2
  Creation Time : Sat Mar 23 11:05:31 2013
     Raid Level : raid5
     Array Size : 9766901760 (9314.44 GiB 10001.31 GB)
  Used Dev Size : 1953380352 (1862.89 GiB 2000.26 GB)
   Raid Devices : 6
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Sat Apr 12 11:23:04 2014
          State : clean 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 2048K

           Name : ubuntu:0  (local to host ubuntu)
           UUID : 0b095b30:b3a5e09d:84b1e96f:53bcbc52
         Events : 28773

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       5       8       80        1      active sync   /dev/sdf
       2       8       32        2      active sync   /dev/sdc
       3       8       64        3      active sync   /dev/sde
       6       8       96        4      active sync   /dev/sdg
       7       8      129        5      active sync   /dev/sdi1

       8       8      113        -      spare   /dev/sdh1




```

---

