---
title: "critical mdadm raid6 array fails to assemble after machine has been shut down a year"
date: 2014-12-31
forum: Server Platforms
---

### Post by Raymond_Peck on 2014-12-31
I have a several-year-old Ubuntu Server which I've had shut down for a year or so.  Last time I had it up my mdadm raid6 was working fine.  Now it doesn't assemble.  It's got 10TB of irreplaceable data on it that I really don't want to lose.  :-)  I'm trying not to panic.

I have notes from when I last rebuilt with a failed drive, on 2011.12.22.  ```
/proc/mdstat
``` showed these drives: ```
sdb[0], sdc[2], sdd[3], sde[5], sdf[6], sdg[1], sdh[7]
```.  Apparently ```
sda[4]
``` had failed.  I rebuilt at that time using:

```
mdadm --manage /dev/md0 -a /dev/sda
``` 

and the array was working for a couple more years.

Now when I boot the machine to copy the data off the array won't assemble:

```
root@supermicro1:~# mdadm --query --detail /dev/md0
**mdadm: md device /dev/md0 does not appear to be active.**
root@supermicro1:~# mdadm --assemble /dev/md0
**mdadm: no devices found for /dev/md0**
root@supermicro1:~# grep ARRAY /etc/mdadm/mdadm.conf
[B]ARRAY /dev/md0 level=raid6 num-devices=8 UUID=294cb54f:764b040c:220a244d:cf5325b0
[/B]root@supermicro1:~# grep DEVICE /etc/mdadm/mdadm.conf
**DEVICE partitions**

```
If I run mdadm -E it shows:

```
root@supermicro1:~# mdadm -E /dev/sd[abcdefgh]
**mdadm: No md superblock detected on /dev/sda.**
**/dev/sdb:**
          Magic : a92b4efc
        Version : 00.90.00
           **UUID : 294cb54f:764b040c:220a244d:cf5325b0** (local to host supermicro1)
  Creation Time : Tue Jul 27 10:35:19 2010
     Raid Level : raid6
  Used Dev Size : 1464832896 (1396.97 GiB 1499.99 GB)
     Array Size : 8788997376 (8381.84 GiB 8999.93 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0


    Update Time : Wed Oct 31 06:36:00 2012
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 2e533d4d - correct
         Events : 35051


     Chunk Size : 128K


      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb


   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       96        1      active sync   /dev/sdg
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
   4     4       8      128        4      active sync
   5     5       8       64        5      active sync   /dev/sde
   6     6       8       80        6      active sync   /dev/sdf
   7     7       8      112        7      active sync   /dev/sdh

and so on, c-h showing like h.
```

It looks to me like I originally built the array on raw disks rather than partitions, and sd[b-h] are still ok.  And that when I rebuilt the array with the new drive in sda it was partitioned rather than a raw drive:

```
 
root@supermicro1:~# fdisk -lu /dev/sd[abcdefgh]


Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006cdf


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          501758    62531583    31014913    5  Extended
**/dev/sda5          501760    62531583    31014912   8e  Linux LVM**


Disk /dev/sdb: 1500.0 GB, 1499989016576 bytes
255 heads, 63 sectors/track, 182363 cylinders, total 2929666048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


**Disk /dev/sdb doesn't contain a valid partition table**
(and c-h the same)
```

mdadm doesn't see any md superblock on any of the sda partitions, even though sfdisk thinks partition 5 is an LVM partition:

```
 
root@supermicro1:~# mdadm -E /dev/sda[12345]
mdadm: No md superblock detected on /dev/sda1.
mdadm: No md superblock detected on /dev/sda2.
**mdadm: No md superblock detected on /dev/sda5.**
root@supermicro1:~

```

I've read a bunch of similar issues here, but I couldn't find one that's exactly the same, so here I am.

I'm not sure why --assemble won't find the devices.  I tried changing the DEVICE line in mdadm.conf to specifically name the device files instead of using "partitions", and that fails too:

```
root@supermicro1:~# mdadm --verbose --assemble /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: /dev/sdf has wrong uuid.
mdadm: cannot open device /dev/sdg: Device or resource busy
mdadm: /dev/sdg has wrong uuid.
mdadm: cannot open device /dev/sdh: Device or resource busy
mdadm: /dev/sdh has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: no devices found for /dev/md0
root@supermicro1:~# 
```

I'm pretty sure the "wrong UUID" message is because the device can't be opened.  mdadm -E shows the same UUID as mdadm.conf.


Any clues?  Will ```
mdadm --create
``` re-do my array or will it destroy things?

---

### Post by MAFoElffen on 2014-12-31
Just curious which version it is still on? And yes, it looks like /dev/sda is not of the same litter.

---

### Post by MAFoElffen on 2014-12-31
This is some of the same on a RAID6
```
root@yann01:/home/username# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdd1[3] sde1[4](S) sda1[0] sdb1[1] sdc1[2]
      8379392 blocks super 1.2 level 6, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```
```

root@yann01:/home/username# mdadm --query --detail /dev/md[0-3]
/dev/md0:
        Version : 1.2
  Creation Time : Fri Dec 26 08:58:59 2014
     Raid Level : raid6
     Array Size : 8379392 (7.99 GiB 8.58 GB)
  Used Dev Size : 4189696 (4.00 GiB 4.29 GB)
   Raid Devices : 4
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Wed Dec 31 17:53:22 2014
          State : clean 
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : yann01:0  (local to host yann01)
           UUID : 4126f29a:26ddb61f:746143c8:ac19802f
         Events : 30

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

       4       8       65        -      spare   /dev/sde1

```
```

root@yann01:/home/username# mdadm -E /dev/sd[a-e][1-7] | egrep 'Event|/dev/sd|State'
/dev/sda1:
          State : clean
         Events : 30
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdb1:
          State : clean
         Events : 30
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          State : clean
         Events : 30
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd1:
          State : clean
         Events : 30
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sde1:
          State : clean
         Events : 30
   Array State : AAAA ('A' == active, '.' == missing)

```
```

root@yann01:/home/username# sudo blkid
/dev/sda1: UUID="4126f29a-26dd-b61f-7461-43c8ac19802f" UUID_SUB="d7596f28-6bc4-fd8f-a336-98db1d24bd8b" LABEL="yann01:0" TYPE="linux_raid_member" 
/dev/sdb1: UUID="4126f29a-26dd-b61f-7461-43c8ac19802f" UUID_SUB="4c55af55-4077-eb17-fb60-44860655f6f0" LABEL="yann01:0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="4126f29a-26dd-b61f-7461-43c8ac19802f" UUID_SUB="963ce9ef-907f-88fe-dbcb-57e5a57ec6db" LABEL="yann01:0" TYPE="linux_raid_member" 
/dev/sdd1: UUID="4126f29a-26dd-b61f-7461-43c8ac19802f" UUID_SUB="16be880d-3ddb-326d-f019-bf57e4bed84a" LABEL="yann01:0" TYPE="linux_raid_member" 
/dev/sde1: UUID="4126f29a-26dd-b61f-7461-43c8ac19802f" UUID_SUB="6a28165a-6296-d049-83c1-2d3ceb3ad122" LABEL="yann01:0" TYPE="linux_raid_member" 
/dev/md0: UUID="42y4hf-Xv3F-lxvb-kPF6-M0q3-yIa9-7xkj5Z" TYPE="LVM2_member" 
/dev/mapper/yann01-yann_root: UUID="625b755b-f444-461d-a3fe-5271fa21dcf6" TYPE="ext4" 
/dev/mapper/yann01-yann_swap: UUID="a6d936ff-3f86-4677-99e9-57d3e2fe8987" TYPE="swap" 

```
Having done that just fro comparison... What I read from your post is that previously you had a problem with /dv/sa and tried to hot-add it in....

Might it be posssible that it didn't take back then? Cause I didn't see it in there. Wha happens if yo tried to force the assemble without /dev/sda present?

---

### Post by Raymond_Peck on 2015-01-01
```

root@supermicro1:~# dmesg
[    0.000000] Linux version 2.6.35-32-server (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #67-Ubuntu SMP Mon Mar 5 21:13:25 UTC 2012 (Ubuntu 2.6.35-32.67-server 2.6.35.14)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.35-32-server root=/dev/mapper/ubuntu1-root ro quiet

```

---

### Post by Raymond_Peck on 2015-01-01
After adding /dev/sda it rebuilt and showed as healthy (this back in 2011).

But: got it!  I figured out how to get the array assembled (but without sda):

I thought the initial problem was that when it tried to assemble mdadm was getting "Device or resource busy".  I had no idea who could be holding onto the devices, and felt that the array would assemble if it didn't run into that, since everything else looked ok.

/proc/mdstat showed the array as inactive.  But, thought I, maybe mdadm is holding the devices anyway?  So I did:

```
mdadm --stop /dev/md0
mdadm --verbose --assemble /dev/md0
```

and it worked!  YAY!

I still have no idea why it wouldn't assemble at boot time and showed inactive, but I'm now able to get my data off (as long as I do it before two drives fail, knock wood).  mdadm -a of /dev/sda5 doesn't work, which is a bit scary.  :-)

---

### Post by MAFoElffen on 2015-01-01
> 
But: got it! I figured out how to get the array assembled (but without sda)

I thought that was what I recommended
> 
What happens if you tried to force the assemble without /dev/sda present?

No worries... good job.

The why (you asked)-- Because /dev/sda didn't have a partition the same size as the others, nor of a type "fd'.... It looked like an LVM default install of a system on a single disk, instead of member of your ARRAY. Before adding that back into the array, I would use fdisk or parted and make that so on that disk (doesn't seem like what is on there is of recent interest).

Now would be a good time to mark this thread as "[COLOR=#ff0000]Solved[/COLOR]"... then to bring that system version up to date? To a recent LTS, right? There were changes to mdadm that were greatly improved since Ubuntu 2.6.35-32.67-server.

---

### Post by Raymond_Peck on 2015-01-02
> **MAFoElffen said:**
> I thought that was what I recommended

What you recommended (dropping sda) wasn't the fix.  The fix was realizing that
the devices were locked because madadm locked them, even though it showed the
array as inactive.  I sure didn't expect that it would lock the devices in an inactive
array!  I had to --stop the inactive array and then --assemble it.

Thanks, though!

---

### Post by MAFoElffen on 2015-01-02
okay, good then.

---

