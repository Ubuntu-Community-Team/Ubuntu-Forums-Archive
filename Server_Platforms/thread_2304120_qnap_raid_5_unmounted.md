---
title: "qnap raid 5 unmounted"
date: 2015-11-24
forum: Server Platforms
---

### Post by Stephen_Radford on 2015-11-24
I have a QNAP TS559Pro, I want to increase the volume on drive one, so I replaced a 2Tb with a 3Tb and allowed it to sync itself then expanded using the system button, this give me a message saying it had failed so I put the 2Tb back in.
When I restarted the system it synced the drives.
I did cat /proc/mdstat and got this back
[/etc] # cat /proc/mdstat
 Personalities : [linear] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4] [multipath]
 md0 : active raid5 sda3[5] sdd3[4] sde3[3] sdc3[2] sdb3[1]
                  7807782144 blocks super 1.0 level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]
 

 md5 : active raid1 sde2[5](S) sdd2[4](S) sdc2[3](S) sdb2[2] sda2[0]
                  530128 blocks super 1.0 [2/2] [UU]
 

 md13 : active raid1 sda4[0] sdd4[5] sde4[6] sdc4[4] sdb4[3]
                  458880 blocks super 1.0 [5/5] [UUUUU]
                  bitmap: 0/8 pages [0KB], 32KB chunk
 

 md9 : active raid1 sda1[0] sde1[8] sdd1[7] sdc1[6] sdb1[5]
                  530112 blocks super 1.0 [5/5] [UUUUU]
                  bitmap: 0/9 pages [0KB], 32KB chunk
 

 unused devices: <none>

I also did this

[/etc] # mdadm --detail /dev/md0
 /dev/md0:
         Version : 01.00.03
   Creation Time : Tue Nov 10 09:23:15 2015
      Raid Level : raid5
      Array Size : 7807782144 (7446.08 GiB 7995.17 GB)
   Used Dev Size : 1951945536 (1861.52 GiB 1998.79 GB)
    Raid Devices : 5
   Total Devices : 5
 Preferred Minor : 0
     Persistence : Superblock is persistent
 

     Update Time : Mon Nov 23 21:09:34 2015
           State : clean
  Active Devices : 5
 Working Devices : 5
  Failed Devices : 0
   Spare Devices : 0
 

          Layout : left-symmetric
      Chunk Size : 64K
 

            Name : 0
            UUID : 0f2c1aa8:a9c55967:9116730f:43b535c7
          Events : 3667
 

     Number   Major   Minor   RaidDevice State
        5       8        3        0      active sync   /dev/sda3
        1       8       19        1      active sync   /dev/sdb3
        2       8       35        2      active sync   /dev/sdc3
        3       8       67        3      active sync   /dev/sde3
        4       8       51        4      active sync   /dev/sdd3

There doesn't appear to anything wrong with raid 5 unless I am missing something.
but it is not mounting.
I have tried mounting using "mount /dev/md0 /share/MD0_DATA"
There is no line in mtab or fstab to mount the volume.
HELP, what am I missing.

---

### Post by darkod on 2015-11-24
Do you have a filesystem on it? Double check it with something like:
```
sudo parted /dev/md0 print
sudo blkid
```

---

### Post by Stephen_Radford on 2015-11-24
the QNAP does not recognise "sudo" and "parted"
[~] # parted /dev/md0 print
Error: /dev/md0: unrecognised disk label.
How else can I check? (Newish to linux)

---

### Post by darkod on 2015-11-24
Hmmm... If it has limited linux commands depending on its firware, you might have better luck on some QNAP forum or their support.

---

