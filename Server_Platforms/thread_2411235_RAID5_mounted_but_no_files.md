---
title: "RAID5 mounted but no files"
date: 2019-01-27
forum: Server Platforms
---

### Post by brakiss on 2019-01-27
So I borked my ubuntu installation and I have reinstalled. My first RAID5 is not showing files. Before I had 9.7TB free now I have 11TB free so something happened and there is not files showing. md0 is the issue, md1 is fine. Here is 

sudo mdadm --detail /dev/md0 

/dev/md0:
           Version : 1.2
     Creation Time : Mon Jun 11 20:26:17 2018
        Raid Level : raid5
        Array Size : 15627789184 (14903.82 GiB 16002.86 GB)
     Used Dev Size : 7813894592 (7451.91 GiB 8001.43 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Sun Jan 27 10:57:19 2019
             State : active 
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 64K

Consistency Policy : bitmap

              Name : Kodi-Server:0  (local to host Kodi-Server)
              UUID : 543514bb:3f675828:a062e0d5:6c088df0
            Events : 107014

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       48        2      active sync   /dev/sdd

Followed by

cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md1 : active raid5 sdh[4] sdg[2] sdf[1] sde[0]
      5860147200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

md0 : active raid5 sdc1[1] sdb1[0] sdd[2]
      15627789184 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      bitmap: 3/59 pages [12KB], 65536KB chunk

unused devices: <none>

Any Ideas? This ws my media drive and I didnt sleep last night thinking I toasted it.

---

### Post by darkod on 2019-01-27
When you say you reinstalled, that means you did not create new md0 array, right?

If you told it to mount the same md0 array without formatting it, the data should be there. I see the array is 16TB. You say it shows 11TB free so that means it does show some data, right?

---

