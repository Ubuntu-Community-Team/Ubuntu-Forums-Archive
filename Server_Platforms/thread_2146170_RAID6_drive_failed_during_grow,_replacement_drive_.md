---
title: "RAID6 drive failed during grow, replacement drive stuck as spare"
date: 2013-05-17
forum: Server Platforms
---

### Post by sierraEcho on 2013-05-17
I was trying to add a new drive onto a 9 drive RAID6 array. The new drive was pre-tested and was fine, worked when I did the "mdadm --add", but suffered a mechanical failure after running the "mdadm --grow" in the middle of the array reshape. Reshape completed successfully, leaving me with a 10 drive array with only 9 members. So far so good. I "mdadm --remove"d the new failed drive, got a brand new replacement, partitioned, tested and tried to add it into the array ("mdadm --add"). Unfortunately this resulted in

```
/dev/md126:
        Version : 1.2
  Creation Time : Wed Nov 28 11:23:17 2012
     Raid Level : raid6
     Array Size : 23441068032 (22355.15 GiB 24003.65 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 10
  Total Devices : 10
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Fri May 17 20:26:15 2013
          State : active, degraded 
 Active Devices : 9
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : xerosis:0
           UUID : bef24ee5:81450e0c:36d18cb7:c507b23c
         Events : 168669

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       7       8       49        1      active sync   /dev/sdd1
       2       8      161        2      active sync   /dev/sdk1
       3       8      113        3      active sync   /dev/sdh1
       4       8       97        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdf1
       6       8       65        6      active sync   /dev/sde1
       8       8      145        7      active sync   /dev/sdj1
       9       8      129        8      active sync   /dev/sdi1
       9       0        0        9      removed

      10       8      177        -      spare   /dev/sdl1

```

Only thing in kern.log after the add was run was

```

May 17 20:04:24 myelo kernel: [8070798.335857] md: bind<sdl1>

```

Tried --fail and --remove on the new drive, followed by another --add, with the same result. 

Removing the new drive, doing a --zero-superblock on the removed drive and adding it back in, no change. 

System is an active server, and the md array is working just fine right now, so we're reluctant to offline the array to try doing an --assemble, which is the only thing I can think to do next. Anyone else got a better idea?

Thanks

---

### Post by SaturnusDJ on 2013-05-18
Maybe you need to run
```
mdadm /dev/md0 --remove detached
```
because the 10th device is still at a removed state.

Otherwise try:
```
mdadm --grow /dev/md0 --raid-devices=10
```
Sound a bit silly because that's already the case, but maybe it will force a sync.

---

### Post by sierraEcho on 2013-05-19
Hi SaturnusDJ, thanks for the reply. 

Tried the "--remove detached", but no change, successful exit from the command but no output and nothing in kern.log either. Adding in a '-v' didn't improve the feedback. I'd actually tried doing '--grow --raid-devices=10' before I posted, forgot to mention it in my post, all that gives me is 

```

mdadm: /dev/md126: no change requested

```

---

### Post by sierraEcho on 2013-05-19
Ah, think I got it. As root I ran

```

echo check>/sys/block/md126/md/sync_action

```

This now gives me the following output from cat /proc/mdstat

```

md126 : active raid6 sdl1[10] sdk1[2] sdh1[3] sdd1[7] sdj1[8] sdi1[9] sdg1[4] sdf1[5] sde1[6] sdc1[0]
      23441068032 blocks super 1.2 level 6, 512k chunk, algorithm 2 [10/9] [UUUUUUUUU_]
      [>....................]  recovery =  0.0% (332652/2930133504) finish=733.9min speed=66530K/sec
      bitmap: 19/22 pages [76KB], 65536KB chunk

```

So, we've got a resync running, but has it taken in the 'spare' drive?

```

# mdadm --detail /dev/md126
/dev/md126:
        Version : 1.2
  Creation Time : Wed Nov 28 11:23:17 2012
     Raid Level : raid6
     Array Size : 23441068032 (22355.15 GiB 24003.65 GB)
  Used Dev Size : 2930133504 (2794.39 GiB 3000.46 GB)
   Raid Devices : 10
  Total Devices : 10
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sun May 19 18:11:46 2013
          State : active, degraded, recovering 
 Active Devices : 9
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

 Rebuild Status : 0% complete

           Name : xerosis:0
           UUID : bef24ee5:81450e0c:36d18cb7:c507b23c
         Events : 187770

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       7       8       49        1      active sync   /dev/sdd1
       2       8      161        2      active sync   /dev/sdk1
       3       8      113        3      active sync   /dev/sdh1
       4       8       97        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdf1
       6       8       65        6      active sync   /dev/sde1
       8       8      145        7      active sync   /dev/sdj1
       9       8      129        8      active sync   /dev/sdi1
      10       8      177        9      spare rebuilding   /dev/sdl1

```

Yes!

Will see tomorrow if that completes successfully and we're back to a clean array. Hopefully this post helps someone else in the future, as some of the other options I was having to consider were far from pretty/safe/elegant/career destroying. Thanks for the assist.

---

### Post by sierraEcho on 2013-05-20
Array now sync'd and clean on 10 drives, so command in my last post did solve the problem. Thanks.

---

