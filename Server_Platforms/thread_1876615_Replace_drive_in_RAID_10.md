---
title: "Replace drive in RAID 10"
date: 2011-11-06
forum: Server Platforms
---

### Post by infecticide on 2011-11-06
Hey Folks,

I had a flaky drive lockup my RAID array this morning so I have removed it and replaced it with a new one.

I have attempted to re-add it to the RAID array but when I look in /proc/mdstat it shows up with a "[S]" next to it, which I assume means Spare.

I need this drive to take its rightful place in the array as an active member.   Does the re-sync need to finish before this can happen or have I missed a step in making it active?


This is what I'm seeing:

mdadm --examine /dev/sdh1

```

[root@fluidic ~]# mdadm --examine /dev/sdh1
/dev/sdh1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 6045e564:dff5474c:c736351b:9b18d8e1
  Creation Time : Mon Oct 24 07:02:25 2011
     Raid Level : raid10
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Sun Nov  6 11:24:22 2011
          State : active
 Active Devices : 7
Working Devices : 8
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 2354ed04 - correct
         Events : 658814

         Layout : near=2
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     8       8      113        8      spare   /dev/sdh1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       0        0        6      faulty removed
   7     7       8      129        7      active sync   /dev/sdi1
   8     8       8      113        8      spare   /dev/sdh1

```



/proc/mdstat


```

[root@fluidic ~]# cat /proc/mdstat
Personalities : [raid10]
md0 : active raid10 sdh1[8](S) sdi1[7] sdf1[5] sde1[4] sdb1[1] sda1[0] sdc1[2] sdd1[3]
      3907039744 blocks 64K chunks 2 near-copies [8/7] [UUUUUU_U]
      [>....................]  resync =  4.4% (173797440/3907039744) finish=60277.2min speed=1031K/sec

unused devices: <none>

```

---

### Post by rubylaser on 2011-11-06
Your spare should be re-added once the sync finishes. 1031K/sec is ridiculously slow though, that's about 42 days to re-sync.

---

### Post by docbop on 2011-11-06
If you had hot spares your bad drive was replaced by one of your hot spares.   So unless you really know your hardware, best to just let the spare resync and replace the bad drive.   If you really feel you have to use the same drive bay then read your RAID doc it should have a procedure for swapping drives.

With RAID 10 you have a lot of redundancy and if most your hardware is identical then I'd leave things along.  If your RAID software has hot-spot monitoring, just monitor your RAID sets and that will tell you if you need to move drives around.

---

