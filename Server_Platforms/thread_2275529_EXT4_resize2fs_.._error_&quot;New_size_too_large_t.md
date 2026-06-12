---
title: "EXT4 resize2fs .. error &quot;New size too large to be expressed in 32 bits&quot;"
date: 2015-04-26
forum: Server Platforms
---

### Post by oehq on 2015-04-26
Hello,

I am running Ubuntu 14.04.2 LTS  64bit
Codename:	trusty


I have expanded  my mdadm raid6 up to 8 - 3tb drives and all looks to have worked great.
however, I am now trying to expand the file system  using "resize2fs" to use the full raid partition but I am getting the error
 "New size too large to be expressed in 32 bits"

Is there anyway to expand the file system to use all the space?   
any help is greatly appreciated


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

jph@heffsvr2:~$ sudo resize2fs /dev/md0
[sudo] password for jph: 
resize2fs 1.42.9 (4-Feb-2014)
resize2fs: New size too large to be expressed in 32 bits

jph@heffsvr2:~$ uname -m
x86_64


XXXXXXXXXXXXXXXXXXXXX  dev/md0  raid Details  XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

jph@heffsvr2:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jul  4 12:59:20 2014
     Raid Level : raid6
     Array Size : 17580804096 (16766.36 GiB 18002.74 GB)
  Used Dev Size : 2930134016 (2794.39 GiB 3000.46 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Sun Apr 26 18:59:43 2015
          State : active, resyncing 
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

  Resync Status : 66% complete

           Name : heffsvr:0
           UUID : 63a964cb:cde1562c:a35bcaec:a9818c51
         Events : 25022

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       49        1      active sync   /dev/sdd1
       2       8        1        2      active sync   /dev/sda1
       3       8       65        3      active sync   /dev/sde1
       4       8       33        4      active sync   /dev/sdc1
       5       8       17        5      active sync   /dev/sdb1
       7       8       96        6      active sync   /dev/sdg
       8       8      113        7      active sync   /dev/sdh1
jph@heffsvr2:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sde1[3] sdf1[0] sdh1[8] sdg[7] sdb1[5] sdc1[4] sda1[2] sdd1[1]
      17580804096 blocks super 1.2 level 6, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]
      [===============>.....]  resync = 77.3% (2267904288/2930134016) finish=169.5min speed=65092K/sec
      
unused devices: <none>


jph@heffsvr2:~$ sudo resize2fs /dev/md0
[sudo] password for jph: 
resize2fs 1.42.9 (4-Feb-2014)
resize2fs: New size too large to be expressed in 32 bits

---

### Post by sandyd on 2015-04-26
Looks like you've passed the 16TB limit.

See [http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/](http://blog.ronnyegner-consulting.de/2011/08/18/ext4-and-the-16-tb-limit-now-solved/) (I don't know if your version is new enough) or move to another FS that supports more than 16TB.

---

### Post by oehq on 2015-04-27
I reviewed this post it's from 2011 ... 4 years old.     [http://blog.ronnyegner-consulting.de...it-now-solved/](http://blog.ronnyegner-consulting.de...it-now-solved/) 

 it says that ext4 was designed for 1024TB maximum (sounds plenty big to me) yet the e2fsprogs tools don't seem to work with the large size raid?.
So I guess I need to rebuild the raid with a different file system?... or have there been changes in the last 4 years that fixed this issue?

Anyone have any suggestions for building raids larger than 16TB?

---

