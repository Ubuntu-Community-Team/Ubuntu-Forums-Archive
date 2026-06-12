---
title: "disk failure during raid recovery"
date: 2011-09-17
forum: Server Platforms
---

### Post by morrn on 2011-09-17
I have a mdadm-controlled raid5 set with 7 1TB-drives.
Yesterday one drive failed

```

$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3] sdh1[6] sdc1[2] sdf1[0] sde1[4] sdi1[1]
      5860559616 blocks level 5, 64k chunk, algorithm 2 [7/6] [UUUUU_U]

unused devices: <none>

```

So i did a shutdown, replaced the faulty disk and booted.
I partitionated the disk, and did a 
```
sudo mdadm /dev/md0 --add /dev/sdg1
```

mdadm begun resyncing ```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdg1[7] sdd1[3] sdh1[6] sdc1[2] sdf1[0] sde1[4] sdi1[1]
      5860559616 blocks level 5, 64k chunk, algorithm 2 [7/6] [UUUUU_U]
      [>....................]  recovery =  0.0% (105048/976759936) finish=619.7min speed=26262K/sec

```

But this morning, when the sync was completed, mdstat shows
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdg1[7](S) sdd1[3] sdh1[6] sdc1[8](F) sdf1[0] sde1[4] sdi1[1]
      5860559616 blocks level 5, 64k chunk, algorithm 2 [7/5] [UU_UU_U]

unused devices: <none>

```

and mdadm -E (see attachment) on the faulty disk shows
```
 
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8       97        7      spare   /dev/sdg1

```

but the other disks report:
```


this     3       8       49        3      active sync   /dev/sdd1

   0     0       8       81        0      active sync   /dev/sdf1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       0        0        5      faulty removed
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8       97        7      spare   /dev/sdg1

```

Edit:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick
$ mdadm --version
mdadm - v2.6.7.1 - 15th October 2008

```

```

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Aug 26 17:05:28 2010
     Raid Level : raid5
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Sep 17 09:22:52 2011
          State : clean, degraded
 Active Devices : 5
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0e288b28:c69e5def:e368bf24:bd0fce41
         Events : 0.115323

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8      129        1      active sync   /dev/sdi1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       0        0        5      removed
       6       8      113        6      active sync   /dev/sdh1

       7       8       97        -      spare   /dev/sdg1
       8       8       33        -      faulty spare   /dev/sdc1


```



Any ideas?

---

