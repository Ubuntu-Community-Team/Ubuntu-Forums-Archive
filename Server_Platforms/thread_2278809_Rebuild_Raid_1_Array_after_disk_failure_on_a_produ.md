---
title: "Rebuild Raid 1 Array after disk failure on a production server (Ubuntu 12.04.2 LTS)"
date: 2015-05-19
forum: Server Platforms
---

### Post by Frederik_Jacobs on 2015-05-19
[COLOR=#111111][FONT=Ubuntu]I manage a production server which has a RAID 1 array with two identical hard drives. Apologies in advance, I've read many threads on this but due to the critical nature of the server, it will save my job if someone can give me accurate step-by-step instructions. As stated, the server is 12.04.2 LTS. One of the drives failed and was replaced by the hosting company. They had to power down the server to replace the hard drive, but now "cat /proc/mdstat" shows its State as "removed" (please see below). I was alerted to the failure by mdadm's daily check and emailed the report:

[/FONT][/COLOR]```
This is an automatically generated mail message from mdadm
running on paris086

A Fail event had been detected on md device /dev/md/0.

It could be related to component device /dev/sdb2.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[1](F) sda2[0]
      499712 blocks super 1.2 [2/1] [U_]
      
md1 : active raid1 sdb3[1](F) sda3[0]
      7995840 blocks super 1.2 [2/1] [U_]
      
md2 : active raid1 sdb4[1](F) sda4[0]
      968130304 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>
```[COLOR=#111111][FONT=Ubuntu]

Here is the current output of "cat /proc/mdstat":

[/FONT][/COLOR]```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] md0 : active raid1 sda2[0]
      499712 blocks super 1.2 [2/1] [U_]
      
md1 : active raid1 sda3[0]
      7995840 blocks super 1.2 [2/1] [U_]
      
md2 : active raid1 sda4[0]
      968130304 blocks super 1.2 [2/1] [U_]

```

and of "df -h":

```
Filesystem      Size  Used Avail Use% Mounted on/dev/md2        909G  782G   82G  91% /
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           1.6G  352K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.8G     0  3.8G   0% /run/shm
/dev/md0        458M   25M  409M   6% /boot
```

Some other (perhaps) useful information:

```
#) fdisk -l


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table


Disk /dev/md2: 991.4 GB, 991365431296 bytes
2 heads, 4 sectors/track, 242032576 cylinders, total 1936260608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md2 doesn't contain a valid partition table


Disk /dev/md1: 8187 MB, 8187740160 bytes
2 heads, 4 sectors/track, 1998960 cylinders, total 15991680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table


Disk /dev/md0: 511 MB, 511705088 bytes
2 heads, 4 sectors/track, 124928 cylinders, total 999424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table
```

```
#) parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1018kB  1000kB                     bios_grub
 2      1018kB  513MB   512MB                      raid
 3      513MB   8705MB  8192MB                     raid
 4      8705MB  1000GB  991GB                      raid




Error: /dev/sdb: unrecognised disk label                                  


Model: Linux Software RAID Array (md)
Disk /dev/md2: 991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4




Model: Linux Software RAID Array (md)
Disk /dev/md1: 8188MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  8188MB  8188MB  linux-swap(v1)




Model: Linux Software RAID Array (md)
Disk /dev/md0: 512MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  512MB  512MB  ext2
```

```
#) cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md2 during installation
UUID=2d22fd63-9d2e-494c-92d9-89f411fb1b5d /               ext4    errors=remount-ro,usrquota 0       1
# /boot was on /dev/md0 during installation
UUID=b99dbfa5-fad2-4ba0-b741-70bd8ddff90e /boot           ext2    defaults        0       2
# swap was on /dev/md1 during installation
UUID=2d72a698-9c6c-4d81-9ed9-3d7ebe544e45 none            swap    sw              0       0
```

Any assistance would be greatly appreciated, as this is a production server. Thank you in advance.

---

### Post by darkod on 2015-05-19
This is normal. Don't panic and don't do anything to make things worse. In mdadm sw raid a rebuild does not start automatically as in hw raid. Up to now this is perfect normal behavior.

I am at work now so unless someone else jumps in I can give you exact commands in a few hours.

Tell me this, do you know to partition a disk with parted?

Also, post more info about current sda layout:
```
sudo parted /dev/sda unit MiB print
sudo parted /dev/sda unit MB print
```

This is because I don't know if sda is partitioned with MB or MiB.

PS. To cover all partitioning options better post this too:
```
sudo parted /dev/sda unit s print
```

That will print the layout in sectors.

---

### Post by Frederik_Jacobs on 2015-05-19
Thanks darkod, appreciate the assist.  Information as requested:

```
sudo parted /dev/sda unit MiB print
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 953870MiB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start    End        Size       File system  Name  Flags
 1      0.02MiB  0.97MiB    0.95MiB                       bios_grub
 2      0.97MiB  489MiB     488MiB                        raid
 3      489MiB   8302MiB    7813MiB                       raid
 4      8302MiB  953870MiB  945568MiB                     raid
```

```
sudo parted /dev/sda unit MB print
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000205MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End        Size      File system  Name  Flags
 1      0.02MB  1.02MB     1.00MB                       bios_grub
 2      1.02MB  513MB      512MB                        raid
 3      513MB   8705MB     8192MB                       raid
 4      8705MB  1000205MB  991500MB                     raid
```

```
sudo parted /dev/sda unit s print
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start      End          Size         File system  Name  Flags
 1      34s        1987s        1954s                           bios_grub
 2      1988s      1001988s     1000001s                        raid
 3      1001989s   17001989s    16000001s                       raid
 4      17001990s  1953525118s  1936523129s                     raid
```

I have used fdisk before when partitioning, though I cannot imagine parted would be more difficult, or are there a trick hidden somewhere that I should keep in mind?

Won't touch the server until I hear from you, thanks again.

---

### Post by darkod on 2015-05-19
The first partition start point is weird, 0.02MB or MiB, so you better use sectors when partitioning sdb. And hope that sdb has at least 1953525118 sectors otherwise you will not be able to create equal partitions on sdb for the raid. That is why when doing the initial install it's better to leave 10-15MiB unused at the end of the disk because disks of "identical" size (like 1TB) are not always identical up to the last sector.

Adding sdb to the raid is fairly simple, the only job you need to do before that is the partitioning. Some people copy the partition table from sda to sdb but I prefer creating the partitions manually for better control.

So, lets start... Open sdb in the parted prompt, make a new gpt table, change the parted unit to sector and print the table data (at this point there will be no partitions, but you can check the total size of sectors).

```
sudo parted /dev/sdb
mklabel gpt
unit s
print
```

If the total sectors are more than the end sector of sda4 from your above post, perfect. Continue creating the partitions identical as on sda. Print the table to confirm the values match.

```
mkpart 34 1987
mkpart 1988 1001988
mkpart 1001989 17001989
mkpart 17001990 1953525118
print
```

If all is good so far, create the flags on each partition as per sda flags.
```
set 1 bios_grub on
set 2 raid on
set 3 raid on
set 4 raid on
```

After that you are all set. Print the table again to compare and confirm all is good, and quit parted.

```
print
quit
```

Now you have sdb with identical partitions as sda.

Just in case, check all arrays to make sure only sda partitions are shown. If any sdb partition is there it will be from the old sdb and needs to be removed first. For each array you can see the details with:
```
sudo mdadm --detail /dev/md0
sudo mdadm --detail /dev/md1
sudo mdadm --detail /dev/md2
```

Only sda[234] should be shown, the sdb slot should say 'removed'.

After that you are ready to add the new sdb partitions. Start with swap (md1) because that is the least important array, to make sure all goes as planned.
```
sudo mdadm /dev/md1 --add /dev/sdb3
```

Now check with cat /proc/mdstat and see if md1 is showing sdb3 as member and that it started syncing. If that is good do the other two arrays:
```
sudo mdadm /dev/md0 --add /dev/sdb2
sudo mdadm /dev/md2 --add /dev/sdb4
```

That's it... check from time to time that md2 sync is going good. That is the largest array and will take longest.

---

### Post by Frederik_Jacobs on 2015-05-21
Thanks Darko, really appreciate your assistance.  I'm in parted and got as far as trying to create the first partition ("mkpart 34 1987") but apparently mkpart requires a part-type parameter as well (primary, logical or extended) and for the life of me I can't figure out how /dev/sda is partitioned - all the tutorials say that if you "print" in parted it should display the Type but my version doesn't. I'm guessing the first partition should be Primary and the others Logical, but I don't want to take any chances.

At least the new /dev/sdb is slightly bigger that sda so that won't be an issue:

```

sudo parted /dev/sda unit s print

Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start      End          Size         File system  Name  Flags
 1      34s        1987s        1954s                           bios_grub
 2      1988s      1001988s     1000001s                        raid
 3      1001989s   17001989s    16000001s                       raid
 4      17001990s  1953525118s  1936523129s                     raid

```

```

sudo parted /dev/sdb unit s print

Model: ATA WDC WD10EZRX-00L (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start  End  Size  File system  Name  Flags


```

---

### Post by darkod on 2015-05-21
For gpt table mkpart does not need partition type. You can put a name before the start value but I wasn't sure if it can be omitted. Just name the partitions anyway you like for example p1-p4. So the mkpart commands would be:
mkpart p1 34 1987
.......etc

Try like that. The name you put has no relevance it's not related to the mount point or anything. You can use names to reflect how you use the array created from that partition, like grub-boot-swap-root. That was the partition order if I remember correctly.

---

### Post by Frederik_Jacobs on 2015-05-21
Thanks Darko, partitioning went great and I've added sdb2 & sdb3 and mdadm -D /dev/md[0,1] shows "State: clean" with both sda2/sdb2 and sda3/sdb3 with "State: active sync".  I'm going to wait until end of business before I do md2 (sdb4) so if something goes wrong then I can spend the night fixing it.  Just out of interest sake, I notice with mdadm -D /dev/md[0,1] there is a "UUID" which differs from the UUID in my /etc/fstab - should I be concerned about that (after I quit parted it gave the following output: "Information: You may need to update /etc/fstab.) ?

```

sudo mdadm -D /dev/md0

/dev/md0:
        Version : 1.2
  Creation Time : Wed Jun 19 12:04:15 2013
     Raid Level : raid1
     Array Size : 499712 (488.08 MiB 511.71 MB)
  Used Dev Size : 499712 (488.08 MiB 511.71 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu May 21 13:36:12 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : paris086:0  (local to host paris086)
**           UUID : ceba0bd5:ffa466c8:7e950165:71dc000d**
         Events : 195


    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       2       8       18        1      active sync   /dev/sdb2

```


```

cat /etc/fstab


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md2 during installation
UUID=2d22fd63-9d2e-494c-92d9-89f411fb1b5d /               ext4    errors=remount-ro,usrquota 0       1
# /boot was on /dev/md0 during installation
**UUID=b99dbfa5-fad2-4ba0-b741-70bd8ddff90e** /boot           ext2    defaults        0       2
# swap was on /dev/md1 during installation
UUID=2d72a698-9c6c-4d81-9ed9-3d7ebe544e45 none            swap    sw              0       0

```

Thanks again, your help has been invaluable!

---

### Post by darkod on 2015-05-21
No, don't touch fstab. That is general message from parted and it depends on what you used it for.
With mdadm the uuid is little strange. You will have uuid assigned to the partition, the md device and the filesystem. If you run sudo blkid you might notice different uuids for sda2 and sdb2 but a joint uuid as part of md0. And then different uuid for the filesystem on md0. This last uuid is the one that goes in fstab.
But you didn't create new arrays, just added a member to them so you don't need to touch fstab.

---

### Post by Frederik_Jacobs on 2015-05-21
Thank you!!

---

### Post by Frederik_Jacobs on 2015-05-22
Darko, you are my hero.  Worked perfectly, thank you very much.

```

cat /proc/mdstat


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[2] sda2[0]
      499712 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sdb3[2] sda3[0]
      7995840 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdb4[2] sda4[0]
      968130304 blocks super 1.2 [2/2] [UU]

```

```

sudo mdadm -D /dev/md2

/dev/md2:
        Version : 1.2
  Creation Time : Wed Jun 19 12:04:15 2013
     Raid Level : raid1
     Array Size : 968130304 (923.28 GiB 991.37 GB)
  Used Dev Size : 968130304 (923.28 GiB 991.37 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Fri May 22 11:12:21 2015
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : paris086:2  (local to host paris086)
           UUID : 2b8bd77e:7fc2806b:56ae349f:01473330
         Events : 1605044


    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       2       8       20        1      active sync   /dev/sdb4

```

---

### Post by darkod on 2015-05-22
Glad you got it sorted out. Perfect.

---

