---
title: "raid5 problems (inactive, spare)"
date: 2009-07-30
forum: Server Platforms
---

### Post by alcazone on 2009-07-30
hi,

i just set up my new home- or fileserver with ubuntu 8.04.3 lts.

I set up a raid 1 during the installation for ubuntu and i try to set up a raid5. The raid 5 works fine for about one day and then i got problems...

md0 is raid 1: /dev/sda1, /dev/sdb1 (using 2 x 80gb hdds) 
md1 is raid 5: /dev/sdc, /dev/sdd, /dev/sde (using 3 x 1tb hdds)


```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0] sdb1[1]
      74918976 blocks [2/2] [UU]

unused devices: <none>
``````

cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=360277c5:ca21a081:a2d915a8:aee05a7e

# This file was auto-generated on Wed, 29 Jul 2009 21:11:46 +0000
# by mkconf $Id$
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=360277c5:ca21a081:a2d915a8:aee05a7e
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=0b8e7fe1:365e1582:01f9e43d:ac30fbff

``````
sudo mdadm -E /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0b8e7fe1:365e1582:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 28 03:14:36 2009
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 1953524992 (1863.03 GiB 2000.41 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Tue Jul 28 23:23:18 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6859ba81 - correct
         Events : 0.88

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       64        3      spare   /dev/sde
``````
sudo mdadm -E /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0b8e7fe1:365e1582:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 28 03:14:36 2009
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 1953524992 (1863.03 GiB 2000.41 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Tue Jul 28 04:11:37 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 6858ac85 - correct
         Events : 0.80

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       48        1      active sync   /dev/sdd

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       48        1      active sync   /dev/sdd
   2     2       0        0        2      faulty removed
   3     3       8       64        3      spare   /dev/sde

``````
sudo mdadm -E /dev/sde
/dev/sde:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0b8e7fe1:365e1582:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 28 03:14:36 2009
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 1953524992 (1863.03 GiB 2000.41 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1

    Update Time : Tue Jul 28 23:23:18 2009
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 1
       Checksum : 6859baa1 - correct
         Events : 0.88

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       64        3      spare   /dev/sde

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       64        3      spare   /dev/sde
jvogel@server:~$

```But i don't want a spare (btw raid 5 can't work with 2 active and 1 spare...)
So i try to remove the spare by using:
```
sudo mdadm /dev/md1 --remove /dev/sde
mdadm: cannot get array info for /dev/md1

```Anybody now what can help?

Thanks for any hint.

---

### Post by fjgaude on 2009-07-30
Stange, it almost seems you have four partitions associated with the raid5 array.

What does the normal health -D commands show:

```
sudo mdadm -D /dev/md1

sudo mdadm -D /dev/md0
```

The UUID for the raid5 seems normal. Strange!

---

### Post by alcazone on 2009-07-30
Hi,

thanks for your reply:

```
sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Jul 29 22:31:16 2009
     Raid Level : raid1
     Array Size : 74918976 (71.45 GiB 76.72 GB)
  Used Dev Size : 74918976 (71.45 GiB 76.72 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jul 30 23:28:34 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 360277c5:ca21a081:a2d915a8:aee05a7e
         Events : 0.13

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```

```
sudo mdadm -D /dev/md1
mdadm: md device /dev/md1 does not appear to be active.

```

I just rebooted the machine and the result for cat /proc/mdstat changed...

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdc[0](S) sde[3](S) sdd[1](S)
      2930287488 blocks

md0 : active raid1 sda1[0] sdb1[1]
      74918976 blocks [2/2] [UU]

unused devices: <none>

```

---

### Post by fjgaude on 2009-07-31
What does your **/etc/fstab** file look like?

Also show this:

```
sudo fdisk -l
```

It will look like something is wrong but **fdisk** doesn't know raid. That's okay. I'm interested to see if the drvie partitions show.

---

### Post by maxix on 2009-08-01
> **alcazone said:**
> 

md1 is raid 5: /dev/sdc, /dev/sdd, /dev/sde (using 3 x 1tb hdds)

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       8       64        3      spare   /dev/sde[/code]

But i don't want a spare (btw raid 5 can't work with 2 active and 1 spare...)
So i try to remove the spare by using:
```
sudo mdadm /dev/md1 --remove /dev/sde
mdadm: cannot get array info for /dev/md1

```Anybody now what can help?

Thanks for any hint.

I just ran out of a similar situation. You have a 3 drives raid array, with two faulty disk, and one of these disks were re-added to the array as a spare.

When the first drive gone bad, the array worked in degraded mode. When you lost the second drive, the array was stopped. You need at least two devices, you have already one active and you need to use one of the faulty drives start again the array.

I don't know wich drive gone off first, nor if it was the drive you mistakely re-inserted in the array as a spare. As the array has probably changed between the first and the second faillure, i suggest to reserve the disk that was down first for later usages.

*edit :  By reading your mdadm -E, i saw that sdc recorded two faillures, sdd one faillures and sde no faillures, so sde was the first to go down, then sdd. So you should use the assemble method with sdc & sdd.*

First you need to stop the array. This can also be done with a simple reboot, as you did.
```
mdadm --stop /dev/md1
```If you want to use the non-spare faulty drive with the active drive, force the assembly. ```
mdadm --assemble --force /dev/md0 /dev/sdc /dev/sdd missing
```Or if you want to get the spare back in the array, re-using existing data on it you'll have to re-create the array, assuming the data is clean and respecting the previous array settings.
```
mdadm --create /dev/md1 --assume-clean --level=5  --chunk=64 --raid-devices=3 /dev/sdc missing /dev/sde
```Now the array should be started, in degraded mode. It is safe to put the array in readonly mode.
```
mdadm --readonly /dev/md1
```You now might want to add a new spare to rebuild the array or backuping data elsewhere, but the array might fall down if the previously faulty drive goes down again. You might then need to recreate the complete array without the missing parameter in order to use the parity stored on all disks to be able to correct read errors, even if the fist down disk is not really up-to-date.[INDENT] Forcing a full assemble won't work because as soon as a disk is marked "spare", it stays spare and no data will be used (i didn't found how to remove the spare flag of a device except modifiing the superblock in raw mode, that's why i use --create --assume-clean) . That's why you shall not use immediately one of the array disk as a spare when you have/risk multiple faillures.
[/INDENT]If the drives gone down because of too much badblocks, you might consider using /usr/share/mdadm/checkarray to force the harddrives to trash the badblocks.

Hope this will help!

---

### Post by alcazone on 2009-08-02
Hi,

thanks for your responses.
 
@fjgaude
```
 sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00070911

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   fd  Linux raid autodetect
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007859a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   fd  Linux raid autodetect
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f246e

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000055a2

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f71cc

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/md0: 76.7 GB, 76717031424 bytes
2 heads, 4 sectors/track, 18729744 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

``````
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=3f0d5494-dae0-4722-86f9-ac222971ce97 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=5b5b0631-dcea-440f-bf07-e3d31f800c23 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

@maxix
i tried the assemble command but get the following error:
```
mdadm --assemble --force /dev/md1 /dev/sdc /dev/sdd missing
mdadm: superblock on /dev/sdd doesn't match others - assembly aborted

```

there isn't any important data on the raid (i haven't any time to copy anything on it), so isn't the easiest and fastest way to remove the raid5 and set it up again?

---

### Post by fjgaude on 2009-08-02
I can't say what is wrong... and if you start over you will have to zero the superblocks of all the drives that have been in an array before. Could be you actually have bad drives, and ones that need to have a filesystem put on them again. Can't say for sure.

Let us know how you do. Thanks!

---

### Post by maxix on 2009-08-02
> **alcazone said:**
> @maxix
i tried the assemble command but get the following error:
```
mdadm --assemble --force /dev/md1 /dev/sdc /dev/sdd missing
mdadm: superblock on /dev/sdd doesn't match others - assembly aborted

```there isn't any important data on the raid (i haven't any time to copy anything on it), so isn't the easiest and fastest way to remove the raid5 and set it up again?
So /dev/sdd seems to be really damaged. You could then try with the other harddrive if you wanted to restore some datas.

If you don't care of the data, sure, erase superblocks, stop the array and create a new array.

---

### Post by johanbach on 2009-08-12
> **maxix said:**
> Or if you want to get the spare back in the array, re-using existing data on it you'll have to re-create the array, assuming the data is clean and respecting the previous array settings.
```
mdadm --create /dev/md1 --assume-clean --level=5  --chunk=64 --raid-devices=3 /dev/sdc missing /dev/sde
```Now the array should be started, in degraded mode. It is safe to put the array in readonly mode.
```
mdadm --readonly /dev/md1
```You now might want to add a new spare to rebuild the array or backuping data elsewhere, but the array might fall down if the previously faulty drive goes down again. You might then need to recreate the complete array without the missing parameter in order to use the parity stored on all disks to be able to correct read errors, even if the fist down disk is not really up-to-date.[INDENT] Forcing a full assemble won't work because as soon as a disk is marked "spare", it stays spare and no data will be used (i didn't found how to remove the spare flag of a device except modifiing the superblock in raw mode, that's why i use --create --assume-clean) . That's why you shall not use immediately one of the array disk as a spare when you have/risk multiple faillures.
[/INDENT]If the drives gone down because of too much badblocks, you might consider using /usr/share/mdadm/checkarray to force the harddrives to trash the badblocks.

Hope this will help!

Will this procedure delete any data on the disks?  I'm having a similar situation and have been unable to get mdadm to assemble the raid.  It seems at least 3/4 drives are okay, so I'm hoping to get the data of the raid (it was my backup when I reinstalled...) and then recreate the raid if I can't recover it.

Thanks!
JB

---

### Post by maxix on 2009-08-12
> **johanbach said:**
> Will this procedure delete any data on the disks?  I'm having a similar situation and have been unable to get mdadm to assemble the raid.  It seems at least 3/4 drives are okay, so I'm hoping to get the data of the raid (it was my backup when I reinstalled...) and then recreate the raid if I can't recover it.

Thanks!
JB

I did it and my datas are alive! The --assume-clean arg ensures the data will be kept -if it is where it should be-. But since i had ten hours between the two faillures, i had a lot of errors on the datas written in the 10 last hours.
Fortunately it was mainly rss feeds in my firefox profile :lolflag: Now i have rss bookmarks that i can't remove or use!

Anyway, this should perhaps work, but be serious, avoid mistakes!

---

### Post by johanbach on 2009-08-13
> **maxix said:**
> I did it and my datas are alive! The --assume-clean arg ensures the data will be kept -if it is where it should be-. But since i had ten hours between the two faillures, i had a lot of errors on the datas written in the 10 last hours.
Fortunately it was mainly rss feeds in my firefox profile :lolflag: Now i have rss bookmarks that i can't remove or use!

Anyway, this should perhaps work, but be serious, avoid mistakes!

Thanks:).  I'll give it a try.  I'm glad it worked for you.  I don't think I wrote anything to the drives recently so I'm assuming most if not all of my data is preserved.

Best,
JB

---

### Post by johanbach on 2009-08-13
I tried it and now I think I cleared it.  I'm at school now, but I'll post my fdisk entry for the raid.  The disk identifier is 000000 (with an x or two somewhere) and it says there isn't a valid partition table.:(

---

### Post by alcazone on 2009-08-13
Hi,

i checked the smart values of the 1tb hdds and yes, as maxis wrote, the /dev/sdd seems to be corrupt.
i get in contact with westerndigital, but this rma needs more time (i have got an american serialnumber and contacted the european support...). :(

However is it possible to first use a raid 1 and convert it to a raid 5, when i get a new hdd?

---

### Post by johanbach on 2009-08-14
You can make a raid5 that is missing a drive and install the drive when it comes.  Unfortunately, this setup does not have data redundancy until the new drive arrives.  As far as converting a raid1 to raid 5, I doubt it is possible, but I've never tried.  I'll let someone else with more knowledge answer authoritatively.

---

### Post by maxix on 2009-08-17
> **johanbach said:**
> I tried it and now I think I cleared it.  I'm at school now, but I'll post my fdisk entry for the raid.  The disk identifier is 000000 (with an x or two somewhere) and it says there isn't a valid partition table.:(
Is it a disk that got no partition table or the array?

Did you try with a missing drive?

---

