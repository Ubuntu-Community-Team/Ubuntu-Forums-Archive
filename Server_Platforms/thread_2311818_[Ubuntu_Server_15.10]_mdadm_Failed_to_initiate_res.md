---
title: "[Ubuntu Server 15.10] mdadm: Failed to initiate reshape!"
date: 2016-01-30
forum: Server Platforms
---

### Post by Speculos on 2016-01-30
Hi,

I've got an 8 disks RAID 5 array I want to expand with 3 more disks, but I can't extend the array, I'm getting the same message everytime:

I am trying to add the first disk it with that command:

```
mdadm --grow /dev/md3 --raid-devices=9 --add /dev/sdi1
```

```
mdadm: Cannot open /dev/sdi1: Device or resource busy
mdadm: Failed to initiate reshape!
```

I'm running Ubuntu Server 15.10 under kernel 4.2.0-25-generic

Here the state of my array with the disk add to the array as spare:


```
mdadm -D /dev/md3
```

```
/dev/md3:
        Version : 1.2
  Creation Time : Fri Oct 23 20:36:02 2015
     Raid Level : raid5
     Array Size : 13673676800 (13040.23 GiB 14001.85 GB)
  Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
   Raid Devices : 8
  Total Devices : 9
    Persistence : Superblock is persistent

    Update Time : Sat Jan 30 15:43:31 2016
          State : clean
 Active Devices : 8
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu-backup:3  (local to host ubuntu-backup)
           UUID : 13e13c34:6cec9c45:e17ebee2:e94c75ce
         Events : 286

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       97        2      active sync   /dev/sdg1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       8       8      113        5      active sync   /dev/sdh1
       6       8       17        6      active sync   /dev/sdb1
       7       8       81        7      active sync   /dev/sdf1

       9       8      129        -      spare   /dev/sdi1


```

```
cat /proc/mdstat
```

```
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10]
md2 : active raid1 sdm3[2] sdk3[1]
      109267776 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sdm2[3] sdk2[2]
      39029760 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdm1[3] sdk1[2]
      7806976 blocks super 1.2 [2/2] [UU]

[B]md3 : active raid5 sda1[0] sdb1[6] sdd1[3] sdc1[1] sdg1[2] sdh1[8] sde1[4] sdf1[7] sdi1[9](S)
      13673676800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [8/8] [UUUUUUUU][/B]

unused devices: <none>

```

I've try with one other disk, and I'm always having the same error message.

I've done the same operation on another server one week ago to an exact same array and it all goes smooth....

Best regards.

Speclulos.

---

### Post by darkod on 2016-01-30
As you can see, sdi1 is already added to the array, as spare. If I'm not mistaken, the reshape takes two steps (at least I would do it in two steps). First add the new partitions to the array, they will become spares automatically.

After that is done, try the grow command. Not in the same command. Why would you run grow and add in same line? You say you want to expand with 3 partitions. First add all three, and then do the grow only once, not three times.

Doing three consecutive grows will be extremely dangerous.

Also, you already have 8 members raid5 array, which is a lot. You want to grow that to 11 members raid5 array? Don't you think that's too many members for a raid5 array that has only single member redundancy?

At last, for such big array dedicated to storage I would advise considering using ZFS, not standard mdadm raid. Or at least think about reshaping to raid6 so that you have two member redundancy.

PS. You have such a big storage and you are running 15.10 which is a non-LTS version and has only 9 months of support??? Unless this is a temporary test system, it is never recommended to run non-LTS for production. Not even for home use.

---

### Post by Speculos on 2016-01-30
I've began by adding the disk (only one partition on the disk) /dev/sdi1 by typing:

```
 mdadm --add /dev/md3 /dev/sdi1
```

I've try to grow the array with two command I've found on Internet:

first:

```
mdadm --grow /dev/md3 --raid-devices=9
```

second (first didn't work)

```
mdadm --grow /dev/md3 --raid-devices=9 --add /dev/sdi1
```

Both result the same way...

Concerning the best practives you have pointed at me: using zfs, using more than 8 disk on RAID 5 array is indeed dangerous, let me tell you that I've synchronise this RAID 5 volume with an another one with the exact same size :lolflag:

Therefore I've indeed notice that I must change to a LTS version of ubuntu server, thanks for the tip :-)

---

### Post by darkod on 2016-01-30
The --grow without the --add should have worked. Unless sdi1 is really busy in another way (mounted, used, etc). But again, if you really want to try this, the correct way is to add all three partitions/disks (I use the term partitions because that's what you are adding to the array, even when there is single partition on the whole disk), and then try the grow like:
```
sudo mdadm --grow /dev/md3 --raid-devices=11 --backup-file=/path/filename
```

It is recommended to use backup file located outside the array you are reshaping because if the reshape goes bad it could help you recover it. But that option is not a requirement.

---

### Post by Speculos on 2016-01-30
OK,

Let's try:

```
sudo mdadm -D /dev/md3
```

```
/dev/md3:
        Version : 1.2
  Creation Time : Fri Oct 23 20:36:02 2015
     Raid Level : raid5
     Array Size : 13673676800 (13040.23 GiB 14001.85 GB)
  Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
   Raid Devices : 8
  Total Devices : 11
    Persistence : Superblock is persistent

    Update Time : Sat Jan 30 17:47:30 2016
          State : clean
 Active Devices : 8
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 3

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu-backup:3  (local to host ubuntu-backup)
           UUID : 13e13c34:6cec9c45:e17ebee2:e94c75ce
         Events : 293

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       97        2      active sync   /dev/sdg1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       8       8      113        5      active sync   /dev/sdh1
       6       8       17        6      active sync   /dev/sdb1
       7       8       81        7      active sync   /dev/sdf1

       9       8      129        -      spare   /dev/sdi1
      10       8      145        -      spare   /dev/sdj1
      11       8      209        -      spare   /dev/sdn1


```

And now let's try to grow the array:

```
sudo mdadm --grow /dev/md3 --raid-devices=11 --backup-file=/root/mdadm_backup-file
```

```
sudo mdadm -D /dev/md3
```

```
/dev/md3:
        Version : 1.2
  Creation Time : Fri Oct 23 20:36:02 2015
     Raid Level : raid5
     Array Size : 13673676800 (13040.23 GiB 14001.85 GB)
  Used Dev Size : 1953382400 (1862.89 GiB 2000.26 GB)
   Raid Devices : 11
  Total Devices : 11
    Persistence : Superblock is persistent

    Update Time : Sat Jan 30 17:49:42 2016
          State : clean, reshaping
 Active Devices : 11
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

 Reshape Status : 0% complete
  Delta Devices : 3, (8->11)

           Name : ubuntu-backup:3  (local to host ubuntu-backup)
           UUID : 13e13c34:6cec9c45:e17ebee2:e94c75ce
         Events : 310

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       97        2      active sync   /dev/sdg1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       8       8      113        5      active sync   /dev/sdh1
       6       8       17        6      active sync   /dev/sdb1
       7       8       81        7      active sync   /dev/sdf1
      11       8      209        8      active sync   /dev/sdn1
       9       8      129        9      active sync   /dev/sdi1
      10       8      145       10      active sync   /dev/sdj1


```

It works !

 :popcorn:

```
cat /proc/mdstat
```

```
Personalities : [raid1] [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid10]
md2 : active raid1 sdm3[2] sdk3[1]
      109267776 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sdm2[3] sdk2[2]
      39029760 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdm1[3] sdk1[2]
      7806976 blocks super 1.2 [2/2] [UU]

[B]md3 : active raid5 sdn1[11] sdg1[2] sdh1[8] sdi1[9] sdj1[10] sde1[4] sdf1[7] sdb1[6] sda1[0] sdd1[3] sdc1[1]
      13673676800 blocks super 1.2 level 5, 512k chunk, algorithm 2 [11/11] [UUUUUUUUUUU]
      [>....................]  reshape =  0.1% (2603520/1953382400) finish=813.7min speed=39951K/sec[/B]

unused devices: <none>


```

Brilliant darkod ! Thanks a lot !

I will post result when reshap will end.

In your previous post you said:

> Doing three consecutive grows will be extremely dangerous.

Why that ?

---

### Post by darkod on 2016-01-30
> Why that?

Because the growing reshape is redoing the layout of the extents/raid on all disks. From 8 members (7 with data plus 1 parity) you want to go to 11 members (10 data + parity) which means it is rewriting the array layout on all disks. Which is very high load on them.

You have raid5 so if two disks fail/drop out the whole array will fail.

That is why doing three consecutive operations of this kind is to be avoided when you can, IMHO. Especially when you can easily add all three members first and then do a single reshape.

---

### Post by Speculos on 2016-01-31
Ok,

I wasn't aware that reshape an array with three disks in the same time could work.

I had bad experience in the past trying add two disk at the same time.

Anyway, I still don't understand why reshape with only one disk didn't worked for me, and with three disks worked...

Finally the job is done, so thank you again darko for your help.

Best regards.

Speculos

---

