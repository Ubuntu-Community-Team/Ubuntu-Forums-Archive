---
title: "Can't grow RAID 6 array after increasing all the disk sizes"
date: 2013-12-13
forum: Server Platforms
---

### Post by max.merrett on 2013-12-13
I've searched 'til I'm blue in the face and can't find an answer so take it easy on me if I've missed it somewhere.

I have a 16TB raid array spanned over 8 3TB disks. It started out as 12TB over 6 full 2TB disks and over the past few months I've increased the number of disks and increased their size while I was at it. After a seemingly endless amount of time resyncing it was time to grow.

```
someone@somewhere:$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Jun 26 23:46:22 2012
     Raid Level : raid6
     Array Size : 11721077760 (11178.09 GiB 12002.38 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Thu Dec 12 17:40:45 2013
          State : active 
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : somewhere:0  (local to host somewhere)
           UUID : c89b0563:1fc12595:965659be:e1769551
         Events : 1451686


    Number   Major   Minor   RaidDevice State
      15       8       81        0      active sync   /dev/sdf1
      14       8       97        1      active sync   /dev/sdg1
       8       8      113        2      active sync   /dev/sdh1
       9       8      145        3      active sync   /dev/sdj1
      12       8      129        4      active sync   /dev/sdi1
      13       8      161        5      active sync   /dev/sdk1
      10       8       33        6      active sync   /dev/sdc1
      11       8       65        7      active sync   /dev/sde1

```



```
sudo mdadm --grow /dev/md0 --size=max
```

and I get 

```
mdadm: component size of /dev/md0 has been set to 1953512960K
```
Exactly what it was.

I found this on the interwebs but it scares the bejeezus out of me [http://unix.stackexchange.com/questions/37293/grow-resize-raid-when-upgrading-visible-size-of-disks](http://unix.stackexchange.com/questions/37293/grow-resize-raid-when-upgrading-visible-size-of-disks). There has to be a way with out locking up, having things crash and the RAID failing.

I've tried a couple of things while replacing the disks like presetting the partition size (0xFD), which madadm doesn't like. I have rebooted to see if that will make it recognise the changes but...

mdadm only sees the 2TB from the partition it created


```
someone@somewhere:/sys/block/md0/md$ grep . dev-sd*/size
dev-sdc1/size:1953513492
dev-sde1/size:1953513441
dev-sdf1/size:1953513424
dev-sdg1/size:1953513441
dev-sdh1/size:1953513475
dev-sdi1/size:1953513458
dev-sdj1/size:1953513475
dev-sdk1/size:1953513458
```

While the system recognises the entire disk:

```
someone@somewhere:$ cat /proc/partitions
major minor  #blocks  name


   8       32 2930266584 sdc
   8       33 1953514516 sdc1
   9        0 11721077760 md0
   8       80 2930266584 sdf
   8       81 1953514448 sdf1
   8       96 2930266584 sdg
   8       97 1953514465 sdg1
   8      112 2930266584 sdh
   8      113 1953514499 sdh1
   8      128 2930266584 sdi
   8      129 1953514482 sdi1
   8      144 2930266584 sdj
   8      145 1953514499 sdj1
   8      160 2930266584 sdk
   8      161 1953514482 sdk1
   8       64 2930266584 sde
   8       65 1953514465 sde1 #editted out disks not in the array
```

Any pointers, help and advice would be greatly appreciated.

I've got one more disk I can play with while replacing (it got cooked. Airflow is important!:mad:).

---

### Post by SaturnusDJ on 2013-12-14
Gpt?

---

### Post by rubylaser on 2013-12-14
I assume you are using an ext4 filesystem and have run into the 16TB limit with the [older e2fsprogs limitations]("http://www.unix-ninja.com/kb/Formatting_Ext4_volumes_beyond_the_16TB_limit/").

---

### Post by max.merrett on 2013-12-14
Yes they are all GPT partition tables.

@rubylaser I can't get the array size to grow in order to run into any ext4 limits. One problem at a time :)

---

### Post by rubylaser on 2013-12-14
Sorry, I saw the 16TB limit and got out my jump to conclusion mat. How did you partition these disks and add them to the existing array?  I ask, because it appears that you just cloned the partition setup from the previous disks.  You need to grow resize the partitions on each disk to take advantage of the wasted space on each one.  Once you do that, the mdadm --grow will actually have more space to grow into.

---

### Post by max.merrett on 2013-12-15
Thanks @rubylaser. I just added the disks into the array and let the defaults go. I failed out one, repartitioned and the added the partition back in to the array instead of the drive. The sizes are now looking correct. I wish I had realised this when I replaced the drives. The resyncing is going to take forever.

---

### Post by rubylaser on 2013-12-16
I'm glad you got it figured out.

---

