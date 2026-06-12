---
title: "Software RAID5 drive active/degraded"
date: 2010-07-20
forum: Server Platforms
---

### Post by pug2694328 on 2010-07-20
Help!  I'm running Ubuntu server 10.04 LTS.  It looks like my software RAID5 is no longer using one of the 5 drives that have been chugging along for several months without problems.  The drives all show up and look healthy in the BIOS.  I just don't know what to do add the 'removed' drive back into the array.

Here's the full output from sudo mdadm -D /dev/md0:
```

/dev/md0:
        Version : 00.90
  Creation Time : Wed May  5 09:47:16 2010
     Raid Level : raid5
     Array Size : 3862494976 (3683.56 GiB 3955.19 GB)
  Used Dev Size : 965623744 (920.89 GiB 988.80 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Jul 20 22:24:25 2010
          State : active, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 24275052:2ca0abe3:38a138f9:68a3106c
         Events : 0.924948

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
       4       0        0        4      removed


```

---

### Post by pug2694328 on 2010-07-22
Nudge.
No thoughts?
Is there a mdadm command to add the drive back into the array?
It hasn't re-added the drive on it's own.
Please help!
Thanks!

---

### Post by richardjh on 2010-07-22
EDIT: There should of course be some disclaimer here about making sure you have backups, be prepared for data loss etc etc etc. 

Looking at the disks there I am assuming that the removed disk is /dev/sdd1 and the drive already has the correct partitions on it as you have said it was previously in the RAID.
You can check that assumption using 

```
sudo fdisk -l
```To add the disk back in use

```
sudo mdadm /dev/md0 --add /dev/sdd1
```It is as easy as that.
You should check the status using
```

sudo mdadm --detail /dev/md0
```And you can watch the rebuild using
```

watch -n1 "cat /proc/mdstat"
```Ctrl+C will exit you from the watch and return you to the command line.

Check out 
```

man mdadm
```For the manual.

By the way, I have in the past re-added failed drives to a RAID, and the drive has ran fine for two years. 
On the other hand the last time I re-added a failed drive it died again that same afternoon, so keep an eye on the RAID for a few days to check the drive is still good, otherwise you may need a replacement.

---

### Post by pug2694328 on 2010-07-23
You RULE richardjh!
Here's the output from 'sudo fdisk -l' confirming that it was previously in the RAID:
```

/dev/sdd1               1      120215   965623808   fd  Linux raid autodetect

```

Here's the output from 'sudo mdadm /dev/md0 --add /dev/sdd1' confirming it is has been readded:
```

mdadm: re-added /dev/sdd1

```

I then ran 'sudo mdadm --detail /dev/md0' and can see that it is rebuilding:
```

/dev/md0:
        Version : 00.90
  Creation Time : Wed May  5 09:47:16 2010
     Raid Level : raid5
     Array Size : 3862494976 (3683.56 GiB 3955.19 GB)
  Used Dev Size : 965623744 (920.89 GiB 988.80 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jul 23 08:51:14 2010
          State : clean, degraded, recovering
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 24275052:2ca0abe3:38a138f9:68a3106c
         Events : 0.979692

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
       5       8       49        4      spare rebuilding   /dev/sdd1

```

Now I'm running 'watch -n1 "cat /proc/mdstat"' and can see the drive is rebuilding into the array:
```

Every 1.0s: cat /proc/mdstat                                                                                                                             Fri Jul 23 08:53:51 2010

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdd5[4] sde5[0] sdb5[2] sdc5[3] sda5[1]
      40619776 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]

md0 : active raid5 sdd1[5] sde1[0] sdb1[2] sda1[1] sdc1[3]
      3862494976 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]
      [>....................]  recovery =  0.8% (8661152/965623744) finish=281.7min speed=56600K/sec

md2 : active raid1 sdb6[1] sdc6[2](S) sda6[0]
      979904 blocks [2/2] [UU]

unused devices: <none>


```

---

### Post by pug2694328 on 2010-07-24
Darn, it looks like it hit a bump in the road.

When I checked this morning using 'sudo fdisk -l' I saw this:

```

/dev/md0:
        Version : 00.90
  Creation Time : Wed May  5 09:47:16 2010
     Raid Level : raid5
     Array Size : 3862494976 (3683.56 GiB 3955.19 GB)
  Used Dev Size : 965623744 (920.89 GiB 988.80 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 24 08:49:24 2010
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 24275052:2ca0abe3:38a138f9:68a3106c
         Events : 0.1010400

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8        1        1      active sync   /dev/sda1
       2       8       17        2      active sync   /dev/sdb1
       3       8       33        3      active sync   /dev/sdc1
       4       0        0        4      removed

       5       8       49        -      faulty spare   /dev/sdd1


```

I tried rerunning the 'sudo mdadm /dev/md0 --add /dev/sdd1' command to re-add the drive, since 'watch -n1 "cat /proc/mdstat"' showed no activity:
```

Every 1.0s: cat /proc/mdstat                            Sat Jul 24 08:56:13 2010

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md1 : active raid5 sdd5[4] sde5[0] sdb5[2] sdc5[3] sda5[1]
      40619776 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]

md0 : active raid5 sdd1[5](F) sde1[0] sdb1[2] sda1[1] sdc1[3]
      3862494976 blocks level 5, 64k chunk, algorithm 2 [5/4] [UUUU_]

md2 : active raid1 sdb6[1] sdc6[2](S) sda6[0]
      979904 blocks [2/2] [UU]

unused devices: <none>


```

but 'sudo mdadm /dev/md0 --add /dev/sdd1' resulted in this ominous message:
```

mdadm: Cannot open /dev/sdd1: Device or resource busy

```

Does this mean I have to order a replacement drive?
Thanks again for all your help!

---

### Post by pug2694328 on 2010-07-25
Followup question.  Assuming I need to replace the drive, are there any tips on determining which of the 5 is the faulty one?

---

### Post by jacekk015 on 2010-07-25
If /dev/sdd is responding then try
```
sudo hdparm -i /dev/sdd - info from boot time
or
sudo hdparm -I /dev/sdd - info directly from disk drive
```You will get then info about disk and serial number - use that to identify.

If you have smartmontools installed you can use:
```
sudo smartctl -i /dev/sdd
```

---

