---
title: "Repair ext3 Filesystem Without Destroying Data [RAID 5 Array]"
date: 2011-12-23
forum: Server Platforms
---

### Post by jmg999 on 2011-12-23
Hi,

I'm running a 7TB fileserver utilizing MD RAID. There are 8 1TB HDDs housed in an external enclosure and connected to the server via two eSATA cables. At one point, one of the cables came undone, and it wreaked havoc on the filesystem. I've tried to repair it, but both the primary and alternative superblocks appear to be unreadable. At this point, the only thing I can think of is to run mke2fs -n /dev/md0, which would not create a new filesystem but would display what it would do if it were to create a new filesystem. 

So, I guess that I have a few questions:

1) Does anyone know how I can pull up the original parameters I'd used to create the ext3 filesystem?

2) Does anyone know a non-destructive way to repair/recreate the filesystem w/out destroying the array itself?

3) Short of the that, does anyone have any experience recreating an ext3 filesystem over the top of an array, where it didn't destroy the data? From what I've read, if the proper parameters are passed to mke2fs, it will recreate the filesystem w/out destroying the underlying data.

Any help would be greatly appreciated. Thank you.


Jeff

---

### Post by CharlesA on 2011-12-23
No backups?

Best bet would be to reformat the [s]drive[/s] array and restore from backups.

---

### Post by jmg999 on 2011-12-23
Unfortunately, I don't have backups of most of the data. Do you have any advice on how to possibly fix it w/out destroying the data?

---

### Post by CharlesA on 2011-12-23
I don't know. I've never had to attempt something like that.

What is wrong with it exactly? Just the missing superblock info?

---

### Post by jmg999 on 2011-12-24
That appears to be the case. Everything I've tried reports back that the superblock info can't be read.

---

### Post by CharlesA on 2011-12-24
Check here:
[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by jmg999 on 2011-12-24
Thanks, I'd seen that page already. I tried mounting w/ alternative superblocks, but apparently, the syntax used in that article is incorrect. I tried this:

sudo mount sb=32768 /dev/md0 /disk2/

But, it gives me a list of possible commands for mount, so I checked the man page. This is what I found referring to the sb option:

sb=n   Instead  of  block  1,  use  block  n as superblock. This could be useful when the
           filesystem has been damaged.  (Earlier, copies of the  superblock  would  be  
           made every  8192  blocks: in block 1, 8193, 16385, ... (and one got thousands 
           of copies on a big filesystem). Since version 1.08, mke2fs  has  a  -s  (sparse  
           superblock) option  to reduce the number of backup superblocks, and since 
           version 1.15 this is the default. Note that this may mean that ext2 filesystems  
           created  by  a  recent mke2fs  cannot  be  mounted r/w under Linux 2.0.*.)  The 
           block number here uses 1k units. Thus, if you want to use logical  block  32768  
           on  a  filesystem  with  4k blocks, use "sb=131072".

I doubt that it will work, since I couldn't recover the superblock for the filesystem w/ the alternative superblocks, but if you know the proper syntax, I'm willing to give it a go.

---

### Post by jmg999 on 2011-12-24
I found the proper syntax (it was missing an -o switch), but it still didn't work.

jeffe@USC:~$ sudo mount -o -sb=131072 /dev/md0 /disk2/
mount: you must specify the filesystem type

---

### Post by rubylaser on 2011-12-24
Is this hardware RAID or mdadm? If it's mdadm, there's a good possibility that your array didn't assemble correctly, and this is the cause of your problems.

---

### Post by CharlesA on 2011-12-24
> **rubylaser said:**
> Is this hardware RAID or mdadm? If it's mdadm, there's a good possibility that your array didn't assemble correctly, and this is the cause of your problems.
They mentioned that it was MD, so I'm guessing it's using mdadm.

---

### Post by rubylaser on 2011-12-24
Jezz, I'm going to chalk me up to missing that to the kid's giving me "Christmas Brain".

---

### Post by CharlesA on 2011-12-24
> **rubylaser said:**
> Jezz, I'm going to chalk me up to missing that to the kid's giving me "Christmas Brain".
Happens to everyone. ;)

Any idea how to reassemble the array?

---

### Post by rubylaser on 2011-12-24
Yeah, but to get started, I'd need the output of...
```
cat /proc/mdstat
```
and
```
mdadm -E /dev/sd[bcdefgh]1
```
^ substitute your devices in place of this.

---

### Post by jmg999 on 2011-12-24
First of all, thank you to all of you trying to help me w/ this problem. I really do appreciate your input. :)

Yes, this is software raid utilizing MD RAID. The problem definitely appears to be the ext3 filesystem and not the RAID filesystem. So, the logical arrangement of the RAID striping appears to be intact, but the ext3 filesystem arranged around it hosed. 

```
sudo dd bs=1024k count=200 if=/dev/md0 of=/tmp/test.out 
200+0 records in
200+0 records out
209715200 bytes (210 MB) copied, 2.86159 s, 73.3 MB/s

ls -la /tmp/test.out
-rw-r--r-- 1 root root 209715200 2011-12-24 13:28 /tmp/test.out

However, running e2fsck and dumpe2fs don't work, b/c the superblocks are corrupt. 

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdg1[5] sdh1[6] sdi1[7] sdd1[2] sde1[3] sdc1[1] sdf1[4] sdb1[0]
      6837319552 blocks level 5, 64k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none>

sudo mdadm -E /dev/sd[b-i]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf3f - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf51 - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf63 - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf75 - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf87 - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       81        4      active sync   /dev/sdf1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdf99 - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8       97        5      active sync   /dev/sdg1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdh1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdfab - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8      113        6      active sync   /dev/sdh1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
/dev/sdi1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 98306771:48f8cd9b:72560c0a:77e3a89a (local to host USC)
  Creation Time : Wed Dec  7 21:40:36 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Dec 23 17:18:31 2011
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4c9cdfbd - correct
         Events : 34

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     7       8      129        7      active sync   /dev/sdi1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1
   4     4       8       81        4      active sync   /dev/sdf1
   5     5       8       97        5      active sync   /dev/sdg1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8      129        7      active sync   /dev/sdi1
```

---

### Post by rubylaser on 2011-12-24
You are correct. Your array appears intact, and the event couter matches on all disks so mdadm is working fine.  If you've tried to mount from all of the alternate superblocks, and it's failed it appears your filesystem may be hosed.

---

### Post by jmg999 on 2011-12-24
Right, so is there any way you know of to repair the ext3 filesystem w/out damaging the array? I was told that if I use the exact parameters I'd used in the initial configuration, running mke2fs again will simply recreate the filesystem in place of the old one w/out destroying the data. Is  this something you're aware of?

---

### Post by rubylaser on 2011-12-25
You can do that with mdadm's create command, but I don't believe you can do that with mke2fs AFAIK.

---

