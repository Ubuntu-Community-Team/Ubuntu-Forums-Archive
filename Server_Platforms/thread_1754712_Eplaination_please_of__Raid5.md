---
title: "Eplaination please of  Raid5"
date: 2011-05-10
forum: Server Platforms
---

### Post by ml41782 on 2011-05-10
Where did my drive space go ? 

I dont think there is anything wrong here . I just setup a media server at home. I decided to do it with a Raid array.  The OS is on its own HD and the media is all on the array. 

I have 5 2TB drives all identical  total 10TB physical

when I setup the raid using mdadm and lvm

I ended up with 7.2TB for the array total. 

I understand there is overhead but 2.8TB ? 



root@media-crypt:~# mdadm -D /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Sat Apr 30 20:30:35 2011
     Raid Level : raid5
     Array Size : 7814051840 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Tue May 10 07:52:13 2011
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : media-crypt:1  (local to host media-crypt)
           UUID : 1f69ff98:54230e6a:a04e0acf:b04d2e48
         Events : 127823

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       4       8       64        3      active sync   /dev/sde
       5       8       80        4      active sync   /dev/sdf
=============
=============

  --- Volume group ---
  VG Name               RAIDSYS
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               7.28 TiB
  PE Size               4.00 MiB
  Total PE              1907727
  Alloc PE / Size       1430795 / 5.46 TiB
  Free  PE / Size       476932 / 1.82 TiB
  VG UUID               D33iex-XdMy-Ea0x-cXhf-w6xJ-nUdY-ORIG2Q
======
======
  --- Logical volume ---
  LV Name                /dev/RAIDSYS/MEDIA_RAID
  VG Name                RAIDSYS
  LV UUID                dydSgY-Ym0c-bU8D-xgk4-LQyu-UtDP-vXgKGr
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                5.46 TiB
  Current LE             1430795
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     8192
  Block device           251:2
=======
=======

---

### Post by rubylaser on 2011-05-10
With RAID5, you lose 1 drive to parity, so you're down to 8TiB right off the bat. Also, hard drive manufacturers quote drive sizes based on base 10, instead of binary, so consumers can get confused by "missing space" with their new hard drives. A 1TB drive has only 931.32GiB of usable space. So, in your case...

(2 * 931.32GiB) * 4 drives = 7450.56 GiB, or ~7.45 TiB, which is exactly what your array size is showing.
```
Array Size : 7814051840 (7452.06 GiB 8001.59 GB)
```

Here's a link if I didn't explain to your satisfaction.
[http://www.ussscctv.com/harddrivesizecapacitiescalculator.aspx]("http://www.ussscctv.com/harddrivesizecapacitiescalculator.aspx")

Also, if you don't mind me asking, what was your reason to put LVM on top of your RAID array?  I ask because I think most people do that because they think that's the only way to resize an array.  Mdadm has those tools built in to allow for future expansion, and disk replacement.

---

