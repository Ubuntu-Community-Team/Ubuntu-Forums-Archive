---
title: "mdadm RAID10 hdd replacement issue - degraded array but spare hdd not failed"
date: 2015-04-24
forum: Server Platforms
---

### Post by akt2 on 2015-04-24
Hi all ):P

Relatively noob on ubuntu server ... as well as this is my first forum post (anywhere ... ever!)

I'm hoping for your insight on an Degraded Array issue on my home 6TB NAS.  I built it a few years ago and switched to ubuntu server platform a few months ago using RAID10.  I received an email from mdadm on a faulty drive ...[INDENT=2][I]"This is an automatically generated mail message from mdadm running on ...

A DegradedArray event had been detected on md device ...
Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdb[0] sdc[1] sde[3] sdd[4](S)
5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]

unused devices: <none>"[/I][/INDENT]
[INDENT]
[/INDENT]

So, I began googling for the best steps to figure out the reason for the DegradedArray.

Here are some diagnostics:

I see /dev/sdd showing up as a **spare**, so I began checking to see why by testing the disks via [B]"smartctl -t short /dev/sd*"
[/B]
I found /dev/sdb & /dev/sdc looking fine ... but the some peculiarity in **/dev/sdd (the spare) **and **/dev/sde (apparently the faulty hdd)**

```
root@-----:~# smartctl -l selftest **/dev/sdd**
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Short offline Completed without error 00% 721 -
# 2 Short offline Completed without error 00% 721 -
# 3 Short offline Completed without error 00% 721 -
# 4 Short offline Completed without error 00% 688 -

root@-----:~# smartctl -l selftest **/dev/sde**
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Short offline Completed: read failure 50% 17051 4136112288
# 2 Short offline Completed: read failure 90% 17038 4136112288
# 3 Short offline Completed: read failure 90% 17038 4136112288
# 4 Short offline Completed: read failure 90% 17038 4136112288
# 5 Short offline Completed: read failure 90% 17005 4136112288
# 6 Extended offline Completed: read failure 90% 17005 4136112288
# 7 Short offline Completed: read failure 90% 17004 4136112288
# 8 Short offline Completed: read failure 30% 16839 4140618424

```

***Now, I'm confused.  Why did the mdadm kick out a seemingly good hdd as a spare and keep the faulty one in the array?***

So, I've been trying to get the Array into a state where I can remove /dev/sde.  But I can only get to a state showing /dev/sdd as spare and not allowing me to appropriately replace /dev/sde.  I've tried too fault, remove, assemble, add, etc. with several variations and error message over the last few days without success.

**Any advice and next steps would be greatly appreciated!!**

Here are some more diagnostics during my last **"mdadm --assemble --scan"** ...

```

root@-----:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdb[0] sdd[4] sde[3] sdc[1]
      5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]
      [====>................]  recovery = 23.8% (697592880/2930135376) finish=264.3min speed=140731K/sec


unused devices: <none>
root@-----:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135376 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Fri Apr 24 09:29:59 2015
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 8K


 Rebuild Status : 23% complete


           Name : -----:-----  (local to host -----)
           UUID : -----
         Events : 104064


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       4       8       48        2      spare rebuilding   /dev/sdd
       3       8       64        3      active sync   /dev/sde
 
root@-----:~# mdadm --examine /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : -----
           Name : -----:----- (local to host -----)
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
   Raid Devices : 4


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270752 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 1296396768 sectors
          State : clean
    Device UUID : -----


    Update Time : Fri Apr 24 09:24:59 2015
       Checksum : 52cbdb6e - correct
         Events : 104063


         Layout : near=2
     Chunk Size : 8K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)


root@-----:~# mdadm --examine /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : -----
           Name : -----:-----  (local to host -----)
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
   Raid Devices : 4


 Avail Dev Size : 5860271024 (2794.40 GiB 3000.46 GB)
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 5860270752 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : -----


    Update Time : Fri Apr 24 09:24:59 2015
       Checksum : 85d01428 - correct
         Events : 104063


         Layout : near=2
     Chunk Size : 8K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)

```

But even after the re-assemble, I still have the /dev/sdd showing up as a spare:

```

root@-----:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdb[0] sdd[4](S) sde[3] sdc[1]
      5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]


unused devices: <none>


root@-----:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135376 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Fri Apr 24 12:37:12 2015
          State : clean, degraded
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 8K


           Name : -----:----- (local to host -----)
           UUID : -----
         Events : 104104


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
       3       8       64        3      active sync   /dev/sde


       4       8       48        -      spare   /dev/sdd

```

---

### Post by darkod on 2015-04-25
The first thing to comment is that you created the array from the whole hdd devices, not partitions. Using partitions is better, and more compatible for the future, because disks are almost never identical in total MiB. A 2TB disk of diffrent models and brands will almost never have identical total MiB. Also for this purpose when creating the partition leave about 15-20MiB unpartitioned at the end, so that in the future it is compatible with "little smaller" disks.

But you can't change that now unless you temporarily move the data, destroy the array and redo it.

You are right, this thing about sdd and sde does look very confusing. Since the smart tests on sde show errors, and you already have sdd as out of the array, you should try doing something fast because if sde fails it might break the array (depending on its position in the raid10 setup).

You said you tried to remove sdd from the array. Was there a specific message why it couldn't do it?

One thing to try is removing it, zeroing the superblock (so that it appears as completely new disk), and adding it again.
```
sudo mdadm /dev/md127 --remove /dev/sdd
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm /dev/md127 --add /dev/sdd
```

See how that goes and post and investigate any error messages.

If that works, you should think about buying a new disk to replace sde.

---

### Post by akt2 on 2015-04-25
Thanks for the response Darko!

Here's how it went:

```

root@-----:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135376 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sat Apr 25 00:36:57 2015
          State : clean, degraded
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 8K


           Name : -----:-----  (local to host -----)
           UUID : -----
         Events : 104169


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
       3       8       64        3      active sync   /dev/sde


       4       8       48        -      spare   /dev/sdd

root@-----:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdb[0] sde[3] sdd[4](S) sdc[1]
      5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]


unused devices: <none>

root@-----:~# sudo mdadm /dev/md127 --remove /dev/sdd
mdadm: hot removed /dev/sdd from /dev/md127

root@-----:~# sudo mdadm --zero-superblock /dev/sdd

root@-----:~# sudo mdadm /dev/md127 --add /dev/sdd
mdadm: added /dev/sdd

root@-----:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdd[4] sdb[0] sde[3] sdc[1]
      5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]
      [>....................]  recovery =  0.0% (2547384/2930135376) finish=325.6min speed=149846K/sec


unused devices: <none>

root@-----:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135376 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sat Apr 25 10:54:50 2015
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 8K


 Rebuild Status : 0% complete


           Name : -----:-----  (local to host -----)
           UUID : -----
         Events : 104172


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       4       8       48        2      spare rebuilding   /dev/sdd
       3       8       64        3      active sync   /dev/sde

```

... and the outcome after rebuild was the same

```

root@-----:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid10 sdd[4](S) sdb[0] sde[3] sdc[1]
      5860270752 blocks super 1.2 8K chunks 2 near-copies [4/3] [UU_U]


unused devices: <none>


root@-----:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Jan 13 18:17:32 2015
     Raid Level : raid10
     Array Size : 5860270752 (5588.79 GiB 6000.92 GB)
  Used Dev Size : 2930135376 (2794.39 GiB 3000.46 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sat Apr 25 15:21:24 2015
          State : clean, degraded
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : near=2
     Chunk Size : 8K


           Name : -----:-----  (local to host -----)
           UUID : -----
         Events : 104228


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       0        0        2      removed
       3       8       64        3      active sync   /dev/sde


       4       8       48        -      spare   /dev/sdd

```

I've decided to back up all my data to a large drive and rebuild the array with RAID 5 and good disks.

Thanks again.

---

