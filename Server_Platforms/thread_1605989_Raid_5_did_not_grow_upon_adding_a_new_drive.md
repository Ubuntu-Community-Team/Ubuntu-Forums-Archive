---
title: "Raid 5 did not grow upon adding a new drive"
date: 2010-10-26
forum: Server Platforms
---

### Post by tubaguy50035 on 2010-10-26
I just grew my raid 5 by adding another 2 TB hard drive.  I now have 5 drives.  I am still only getting 6TB of space.  I can't figure out why.

```
sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.91
  Creation Time : Thu Oct  7 01:08:01 2010
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Oct 25 23:18:06 2010
          State : clean, recovering
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 32K

 Reshape Status : 1% complete
  Delta Devices : 1, (4->5)

           UUID : 42635ab9:53d982c1:114a5004:db5dc082
         Events : 0.7160

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       2       8       81        2      active sync   /dev/sdf1
       3       8       97        3      active sync   /dev/sdg1
       4       8       65        4      active sync   /dev/sde1
```This is the detail for my raid device.  It seems like it should be working but maybe it added the new drive as a spare?  Please help!

---

### Post by dtfinch on 2010-10-26
"Reshape Status : 1% complete"

I haven't used md raid 5, but it'll probably need to finish reshaping before that extra space becomes available. The new space will be at the end of each drive, and until the reshaping is done, the ends of the first 4 drives will be occupied by existing data.

---

### Post by tubaguy50035 on 2010-10-26
Okay.  That is very different from creating the raid.  When I created the raid, I was able to use all 6TB right away.

---

### Post by tubaguy50035 on 2010-10-26
Anybody else have any thoughts?

```
sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.91
  Creation Time : Thu Oct  7 01:08:01 2010
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Oct 26 14:04:08 2010
          State : clean, recovering
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 32K

 Reshape Status : 24% complete
  Delta Devices : 1, (4->5)

           UUID : 42635ab9:53d982c1:114a5004:db5dc082
         Events : 0.17748

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       2       8       81        2      active sync   /dev/sdf1
       3       8       97        3      active sync   /dev/sdg1
       4       8       65        4      active sync   /dev/sde1
```

Here's the current detail showing that the space is not becoming available as the parity is reassigned to their new locations.

---

### Post by BobVila on 2010-10-26
I wouldn't expect the space to dynamically grow as the raid reshapes. Report back when the rebuild is done if you're still having problems. Otherwise, sit tight.

---

### Post by tubaguy50035 on 2010-10-26
Alright.  It just takes so long!  I did try to speed up the raid write speed by setting ... I don't remember what it was... to like 15000, but it still only writes at 8474K/sec.  Is this normal?  I'm using fairly cheap pci cards.  The processor has very little load on it though.

---

### Post by dtfinch on 2010-10-26
You could see if increasing the stripe cache size helps. The default is very small like 128.

"echo 2048 > /sys/block/md0/md/stripe_cache_size"

edit: memory usage in kb is something like stripe_cache_size*4*disks, so 2048 would use 40mb ram.

---

### Post by tubaguy50035 on 2010-10-26
Is this the same as the chunk size?

---

### Post by tubaguy50035 on 2010-10-28
At 79.5% my speed jumped up to 12915K/sec...  any thoughts why that might be?  These five drives are spread out on two different cards.  It could be one card versus the other... but they are the same model.

---

### Post by tubaguy50035 on 2010-10-28
It did update the space available to 8 TB after it finished resyncing.  Any thoughts on the speed increase I mentioned?

---

### Post by jacekk015 on 2010-10-29
echo 50000 >/proc/sys/dev/raid/speed_limit_min

---

