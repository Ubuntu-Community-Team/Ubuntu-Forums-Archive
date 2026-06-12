---
title: "[SOLVED] My degraded raid 5 array will not start"
date: 2008-07-09
forum: Server Platforms
---

### Post by siDDis on 2008-07-09
Yesterday I found a dead disk in my array, today I removed it. However when I booted up my computer the degraided raid didn't mount itself.

First I tried to check its status

```

olav@olav-linux:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdg1[0](S) sdf1[8](S) sda1[7](S) sdb1[6](S) sde1[5](S) sdd1[4](S) sdj1[3](S) sdi1[2](S) sdh1[1](S)
      4395455424 blocks
       
unused devices: <none>

```

So I tried to start it with

```

olav@olav-linux:~$ sudo mdadm --run /dev/md0
mdadm: failed to run array /dev/md0: Input/output error

```

--details displays this:

```
olav@olav-linux:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Jan  8 22:38:46 2008
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 10
  Total Devices : 9
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul  9 20:48:36 2008
          State : active, degraded, Not Started
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : db3fbd24:5b636f9a:861f6929:f70ab52b (local to host olav-linux)
         Events : 0.1070901

    Number   Major   Minor   RaidDevice State
       0       8       97        0      active sync   /dev/sdg1
       1       8      113        1      active sync   /dev/sdh1
       2       8      129        2      active sync   /dev/sdi1
       3       8      145        3      active sync   /dev/sdj1
       4       8       49        4      active sync   /dev/sdd1
       5       8       65        5      active sync   /dev/sde1
       6       8       17        6      active sync   /dev/sdb1
       7       8        1        7      active sync   /dev/sda1
       8       8       81        8      active sync   /dev/sdf1
       9       0        0        9      removed

```

What could be wrong?

---

### Post by siDDis on 2008-07-10
Found out a bit more

```
olav@olav-linux:~$ sudo mdadm --assemble --run --force /dev/md0 /dev/sd[abdefghij]
mdadm: no recogniseable superblock on /dev/sda

```

```

olav@olav-linux:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed404

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cab7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc41ff498

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc3            9730       48641   312560640   83  Linux
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000da77c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003264

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007de4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb13b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a3c0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdj: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00037768

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       60801   488384001   fd  Linux raid autodetect

```

---

### Post by fjgaude on 2008-07-10
I can't say what is wrong... did you -f, fail, i.e., make faulty, then -r, the bad drive before you physcially removed it?

You still have your /etc/mdadm/mdadm.conf file in place?

---

### Post by siDDis on 2008-07-10
I solved this easily with

```
sudo mdadm --assemble --run --force /dev/md0 /dev/sd[abdefghij]**1**
```

;)

---

### Post by fjgaude on 2008-07-10
Very good, only one little number needed to be added...

---

