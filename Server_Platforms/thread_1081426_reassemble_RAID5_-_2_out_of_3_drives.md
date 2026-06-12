---
title: "reassemble RAID5 - 2 out of 3 drives"
date: 2009-02-26
forum: Server Platforms
---

### Post by darvari on 2009-02-26
Hi folks, 

I have an ubuntu-server based NAS for my private files, it features a mdadm-RAID5 out of 3 identical SAMSUNG500GB drives.
Each disk contains a single "linux-raid-autodetect"-partition.
The system boots from a CF-Card.

Yesterday (don't ask how) I managed to stumble and as a result disconnected 2 out of 3 drives and one drive even dropped on the floor. I immediately shut down the pc by power-switch.

1 out of 3 drives is definitely wrecked (gives strange sounds).
The other 2 are recognized correctly by the kernel and I can look at them with i.e. hexedit, or see their partition table with fdisk.

Now I intend to 'assemble' the remaining 2 disks in order to copy data from them which accumulated during the last month (I have an external 1TB backup-harddisk)

I tried several commands in order to get it running, but failed.

Here is what I tried:

```
sudo mdadm --assemble --run --force --verbose /dev/md0 /dev/sdb1 /dev/sda1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 3.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
mdadm: added /dev/sda1 to /dev/md0 as 3
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.
*****************************************************************
sudo mdadm --stop /dev/md0
*****************************************************************
sudo mdadm --assemble  /dev/md0 /dev/sdb1 /dev/sda1       
mdadm: /dev/md0 assembled from 1 drive and 1 spare - not enough to start the array.
*****************************************************************
sudo mdadm --stop /dev/md0
*****************************************************************
sudo mdadm --run /dev/md0 /dev/sdb1 /dev/sda1
mdadm: failed to run array /dev/md0: Invalid argument
mdadm: /dev/sdb1 does not appear to be an md device
mdadm: /dev/sda1 does not appear to be an md device
*****************************************************************
sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 09fe2318:0ab329fe:9042ab97:3e5369e3 (local to host ubuntus)
  Creation Time : Thu Jan 15 21:07:58 2009
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Feb 26 01:14:35 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 3ca6aa42 - correct
         Events : 44444

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       17        3      spare   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       17        3      spare   /dev/sdb1
*****************************************************************
sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 09fe2318:0ab329fe:9042ab97:3e5369e3 (local to host ubuntus)
  Creation Time : Thu Jan 15 21:07:58 2009
     Raid Level : raid5
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Feb 26 01:14:35 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 3ca6aa54 - correct
         Events : 44444

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1
   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       0        0        2      faulty removed
   3     3       8       17        3      spare   /dev/sdb1
*****************************************************************

```
I know I could probably create the raid5-device again from the scratch with 1 missing disk, wait for the resync/rebuild and then probably be able to access the data. But I don't want to risk it yet. 

Any ideas?

---

### Post by kidders on 2009-02-27
Hi there,

> **darvari said:**
> ```
sudo mdadm --assemble  /dev/md0 /dev/sdb1 /dev/sda1
mdadm: /dev/md0 assembled from 1 drive and 1 spare - not enough to start the array.
```Something about your post isn't adding up for me. I know this sounds like a dumb question, but are you *sure* your array only has three devices?

> **darvari said:**
> ```
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 3.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: no uptodate device for slot 2 of /dev/md0
```This suggests you have four disks, not three, and that two of them are missing. One of the two remaining is apparently a spare, so you essentially have 66% data loss, which is beyond the tolerance of RAID 5.

Then again, perhaps I've gone crazy! :confused:

---

### Post by darvari on 2009-03-01
[QUOTE=kidders;6810722]Hi there,

but are you *sure* your array only has three devices?
[QUOTE]

Hi kidders,

thanks for your thoughts on this - it made me wonder too what the hell I must have been doing when creating the raid5. But I definitely created it with 3 devices.
Yesterday I dared to recreate it with on drive 'missing', so I did:
```
mdadm --create /dev/md0 --level=5 --raid-devices /dev/sda1 /deb/sdb1 missing
```and it worked, I could instantly mount it, 'cat  /proc/mdstat' showed no rebuild/resync activity.
and 'mdadm --detail /dev/md0' now reads:
```

/dev/md0:
        Version : 00.90
  Creation Time : Sat Feb 28 17:23:33 2009
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Mar  1 15:25:31 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f7fed6a2:4fe50cc8:9042ab97:3e5369e3 (local to host ubuntus)
         Events : 0.1788

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed
You have new mail in /var/mail/baron
baron@ubuntus:~$ sudo mdadm --detail /dev/md0
[sudo] password for baron:
/dev/md0:
        Version : 00.90
  Creation Time : Sat Feb 28 17:23:33 2009
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Mar  1 15:32:35 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : f7fed6a2:4fe50cc8:9042ab97:3e5369e3 (local to host ubuntus)
         Events : 0.1890

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

```
Those several (4-5) devices in my initial post must have their explanation in me trying several combinations of --assemble --incremental and so on, possibly also mistakenly used other sd-Devices (like the boot-device) which then ended up beeing shown there. Who knows..

---

### Post by kidders on 2009-03-01
Hey again,

Glad you got it sorted. The details you posted still don't make much sense though, so be careful when you're restoring your redundancy! For example, running **mdadm --create /dev/md0 --level=5 --raid-devices /dev/sda1 /deb/sdb1 missing** shouldn't construct an array out of /dev/sdb1 and /dev/sdc1.

Your array won't re-sync itself until you build the redundancy back into it (ie re-add the third disk). You should probably do that as soon as possible.

---

