---
title: "Inspecting newly configured RAID - possible problem?"
date: 2010-12-17
forum: Server Platforms
---

### Post by putz3000 on 2010-12-17
**Background:** I need to setup a storage server for work using software RAID. Due to hardware limitations and user needs, I am attempting to build server using four 1 TB hard drives.  the configuration I went for was three partitions: 16 GB swap, 500 MB boot, everything else.

What I "thought" I did was create four 16 GB partitions, sda1 & sdb2 RAID 1 for swap, sdc1 & sdd1 marked as spare.  

I then "thought" I created four 500 MB partitions, sda2 & sdb2 RAID 1 for Boot, and sdc2 & sdd2 marked as spare.

The final thing I "thought" I did was create 4 partitions with the remaining space.  sda3, sdb3, and sdc3 as RAID 5 with sdd3 marked as spare.

**Where I am at now:**  After install I used commands mdadm -D /dev/md0 as well as md1 and md2.  the information though has me a little confused.

**MD0:** 2 active / 4 working / 2 spare  Listed as RAID 1
Array Size: 15624128 (14.90 GiB 16.00 GB)

Number = 0 Major = 8 Minor = 1 RAID Dev = 0 State = active sync /dev/sda1

Number = 1 Major = 8 Minor = 17 RAID Dev = 1 State = active sync /dev/sdb1

Number = 2 Major = 8 Minor = 49 RAID Dev = - State = spare /dev/sdd1

Number = 3 Major = 8 Minor = 33 RAID Dev = - State = spare /dev/sdc1

**MD1:**  2 active / 3 working / 1 spare  Listed as RAID 1
Array Size: 488384 (477.02 MiB 500.11 MB)

Number = 0 Major = 8 Minor = 2 RAID Dev = 0 State = active sync /dev/sda2

Number = 1 Major = 8 Minor = 18 RAID Dev = 1 State = active sync /dev/sdb2

Number = 2 Major = 8 Minor = 34 RAID Dev = - State = spare /dev/sdc2

**MD2:** 3 active / 4 working / 1 spare  Listed as RAID 1
Array Size: 1921296256 (1832.29 GiB 1967.41 GB)

Number = 0 Major = 8 Minor = 3 RAID Dev = 0 State = active sync /dev/sda3

Number = 1 Major = 8 Minor = 19 RAID Dev = 1 State = active sync /dev/sdb3

Number = 2 Major = 8 Minor = 35 RAID Dev = 2 State = active sync /dev/sdc3

Number = 3 Major = 8 Minor = 51 RAID Dev = - State = spare /dev/sdd3


**My Questions/Thoughts:**  Over all it looks to me like I got most of what I was looking for.  However, it also looks to me like I screwed something up along the way.

1) under MD0, should I be concerned that sdd1 comes before sdc1 for the spare?

2) Under MD1, it looks to me like I screwed up and somehow did not mark sdd2 as a spare.  Is there any way to go back and tell the system that sdd2 is also a spare for /boot?

Thank you,

---

### Post by disabledaccount on 2010-12-17
1) generally - no - this is only numbering and has little meaning for spare drives. However it should be mentioned that replacing the drive means replacing all partitions - in partition based RAIDs it is possible that spare from different drive is used because of bad sectors and not whole drive failure. In some very rare cases numbering can affect drive replacement procedure.
2) you can add/remove spare drives/partitions at any time - read mdadm manual ;)

---

### Post by jbrown96 on 2010-12-17
1) No
2) sudo mdadm --add /dev/md1 /dev/sdd2

---

### Post by putz3000 on 2010-12-17
Thank you both for your input.  This is uncharted territory for me so I appreciate you both answering my questions.  I will look over the mdadm instructions for adding the spare.  

I am glad it should be that easy, was a bit concerned I would have to wipe everything out and try it all again.

---

