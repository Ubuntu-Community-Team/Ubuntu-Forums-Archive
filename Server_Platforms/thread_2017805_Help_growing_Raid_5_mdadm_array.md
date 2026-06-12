---
title: "Help growing Raid 5 mdadm array"
date: 2012-07-05
forum: Server Platforms
---

### Post by blackstripes on 2012-07-05
So I have a raid 5 array set up using mdadm that consists of 3 1TB hard drives mounted at /dev/md0.  I've got an extra 2TB hard drive lying around and I would like to throw it into the mix.  Would I be able to partition off 1TB of that 2TB drive and throw it into the raid5 array and then use the other half of the drive as general storage?  

I've used this guide to set up the initial array:

[http://www.iceteks.com/articles.php/linuxmdadmraid/1](http://www.iceteks.com/articles.php/linuxmdadmraid/1)

...but now I'm a little confused as to how to partition and/or format this 2TB drive.  The steps in that guide aimed at growing the array don't seem to mention anything about formatting new drives, much less prepping a physically larger drive for use in a 3x1TB raid5 like mine. 

Any help would be appreciated.  I don't have my data backed up so I'm trying to be cautious here... :redface:

---

### Post by blackstripes on 2012-07-05
I should note that I initially was going to split the 2TB drive into 1TB partitions, and add them both to the array but realized that if the 2TB drive crapped out it would take my whole raid5 with it... that is true, yes?

---

### Post by spynappels on 2012-07-06
> **blackstripes said:**
> I should note that I initially was going to split the 2TB drive into 1TB partitions, and add them both to the array but realized that if the 2TB drive crapped out it would take my whole raid5 with it... that is true, yes?

That is certainly correct, if the physical 2TB disk failed, it would drop out 2 of the 1TB partitions in the array and that would lead to data failure as RAID5 can only cope with 1 drive (partition) dropping out.

Just as general background, do you have your /boot on a different volume, outside of the RAID5 array?

I think your best option would be to use parted to create 2 partitions on the 2TB drive of 1TB each. Make one of them a linux-raid partition and the other a normal ext4 fs partition which can be mounted anywhere you like.

You should then be able to add the linux-raid partition to the mdadm array and grow it.

Hopefully Rubylaser will come along soon to confirm that this will work, but AFAIK, it should be fine.

---

### Post by blackstripes on 2012-07-06
No, my /boot is on a separate SSD, this raid5 is storage.

I think I understand the partitioning at a high level, but I don't have a grasp on the step by step.  I presume I'd want to use something like fdisk, but I get lost when it comes to sizing the partition and decided where they are physically located on the disk (sectors, etc.).

---

### Post by rubylaser on 2012-07-06
If you followed that guide, you are using whole disks rather than partitions.  To use your 2TB drive, you'll want to partition the drive into 2 1TB partitions.  You can use fdisk for that.  Give me a few minutes, and I'll mockup an example in Virtualbox to show you the steps.  Can you give us the output of these commands (this assumes your mdadm device is /dev/md0)?

```
mdadm --detail /dev/md0
```
```
fdisk -l
```

---

### Post by blackstripes on 2012-07-06
Sure here you go:

```
/dev/md0:
        Version : 1.2
  Creation Time : Sun Apr 29 20:04:55 2012
     Raid Level : raid5
     Array Size : 1953522688 (1863.02 GiB 2000.41 GB)
  Used Dev Size : 976761344 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Jul  6 07:45:16 2012
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : fileserver:0
           UUID : ccfd3103:c2db2111:129b52e1:6d5b8fc3
         Events : 43

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       3       8       64        2      active sync   /dev/sde
```

For some reason fdisk -l doesn't do anything.  When I hit return i'm taken to a next line in the bash prompt.

---

### Post by blackstripes on 2012-07-06
Whoops, I wasn't running fdisk -l as root, here you go:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   781422767   390711383+  ee  GPT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000467ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108271615    54134784   83  Linux
/dev/sdb2       108273662   125044735     8385537    5  Extended
/dev/sdb5       108273664   125044735     8385536   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  1953525167   976762583+  fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders, total 3907045376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1  3907029167  1953514583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

---

### Post by blackstripes on 2012-07-06
FYI, the 64GB SSD is Ubuntu and the 400GB drive is OS X. I'd like to leave them alone. :)

---

### Post by rubylaser on 2012-07-06
Let's assume that your mdadm device currently looks like this (except I used 1GB disks instead of 1TB disks).
```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jul  6 08:59:17 2012
     Raid Level : raid5
     Array Size : 2096128 (2047.34 MiB 2146.44 MB)
  Used Dev Size : 1048064 (1023.67 MiB 1073.22 MB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Fri Jul  6 09:00:58 2012
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : test:0  (local to host test)
           UUID : 663bfa0d:46be2621:8ec37b37:39a16205
         Events : 26

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       3       8       48        2      active sync   /dev/sdd
```

First, you'll want to fdisk your new 2TB drive (it will be /dev/sde in my example). 
**[COLOR="Red"]You'll want to change the +1G to +1000G in your example. Or make it match the sector count of one of your 1TB drives.[/COLOR]**
```
fdisk /dev/sde

Command (m for help): [COLOR="red"]n[/COLOR]
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): [COLOR="Red"]p[/COLOR]
Partition number (1-4, default 1): [COLOR="red"]1[/COLOR]
First sector (2048-4194303, default 2048): [COLOR="red"]2048[/COLOR]
Last sector, +sectors or +size{K,M,G} (2048-4194303, default 4194303): [COLOR="red"]+1G[/COLOR]

Command (m for help): [COLOR="red"]t[/COLOR]
Selected partition 1
Hex code (type L to list codes): [COLOR="red"]fd[/COLOR]
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): [COLOR="red"]n[/COLOR]
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): [COLOR="red"]p[/COLOR]
Partition number (1-4, default 2): [COLOR="red"]2[/COLOR]
First sector (2099200-4194303, default 2099200): [COLOR="red"]Hit Enter[/COLOR]
Last sector, +sectors or +size{K,M,G} (2099200-4194303, default 4194303): [COLOR="red"]Hit Enter[/COLOR]

Command (m for help): [COLOR="red"]t[/COLOR]
Partition number (1-4): [COLOR="red"]2[/COLOR]
Hex code (type L to list codes): [COLOR="red"]83[/COLOR]

Command (m for help): [COLOR="red"]w[/COLOR]
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

You'll end up with 2 partitions on your 2TB disk and be ready to add the 1st partition to the array (/dev/sde1).
```
Disk /dev/sde: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders, total 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000efab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048     2099199     1048576   fd  Linux raid autodetect
/dev/sde2         2099200     4194303     1047552   83  Linux

```

You can add the new partition like this.
```
mdadm --add /dev/md0 /dev/sde1
```

Then, add the 4th device
```
mdadm --grow /dev/md0 --raid-devices=4
```

Then, you can watch it grow.
```
watch cat /proc/mdstat
```

Your array should now look like this.
```
root@test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jul  6 08:59:17 2012
     Raid Level : raid5
     Array Size : 3144192 (3.00 GiB 3.22 GB)
  Used Dev Size : 1048064 (1023.67 MiB 1073.22 MB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Fri Jul  6 09:37:34 2012
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : test:0  (local to host test)
           UUID : 663bfa0d:46be2621:8ec37b37:39a16205
         Events : 54

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       3       8       48        2      active sync   /dev/sdd
       **4       8       65        3      active sync   /dev/sde1**
```

When it's done, I like to unmount my array, and run an fsck on the filesystem before I grow it (let's say I have it mounted on /storage).
```
umount /storage
```
```
fsck.ext4 /storage
```

When that's done, grow the filesystem.
```
resize2fs /dev/md0
```

Finally, remount the array.
```
mount -a
```

Next, you'll need to create a filesystem on your second partition.
```
mkfs.ext4 /dev/sde1
```

And create and /etc/fstab entry for it and mount it. Obviously, the devices I've mentioned above could be different than your system, but hopefully this gives you a good idea of what I mean.

---

### Post by spynappels on 2012-07-06
> **rubylaser said:**
> 
```
mkfs.ext4 /dev/sde1
```


/dev/sde2 I think...

Told you Rubylaser would put you right though, he's the RAID guru!

---

### Post by blackstripes on 2012-07-06
Thank you very much for your assistance.  Here is me running fdisk on /dev/sdf

```
root@pzwolinski-EP45-UD3L:~# fdisk /dev/sdf

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (7-3907029167, default 7): 2048
Last sector, +sectors or +size{K,M,G} (2048-3907029167, default 3907029167): +1000G

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 2
First sector (7-3907029167, default 7): 
Using default value 7
Last sector, +sectors or +size{K,M,G} (7-2047, default 2047): 
Using default value 2047

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

..and here is the output of fisk -l afterwards:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   781422767   390711383+  ee  GPT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000467ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108271615    54134784   83  Linux
/dev/sdb2       108273662   125044735     8385537    5  Extended
/dev/sdb5       108273664   125044735     8385536   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  1953525167   976762583+  fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders, total 3907045376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  2097154046  1048575999+  fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.
/dev/sdf2               7        2047        1020+  83  Linux

Partition table entries are not in disk order

```

Does this look right?  Here is the drive in disk utility:
[IMG]https://dl.dropbox.com/u/35008053/Screenshot%20from%202012-07-06%2008%3A53%3A11.png[/IMG]

---

### Post by rubylaser on 2012-07-06
You're going to want to remove your partition from your 2TB drive and remove the GPT label if you want to follow my instructions just for clarity's sake.

```
parted /dev/sdf
```
2. Once inside parted type "mktable" <-- without the quotes
-> Table type: msdos
-> Destroy data: yes
-> quit
3. GPT should now be removed.

No, that doesn't look right, you have extra sectors used on your 2TB disk.  Why don't you delete the two partitions on it like this.
Next, you can run fdisk on that disk.
```
fdisk /dev/sdf
```
Press d to delete the first partition
Then press w to write.

Then where you used the +1000G before in fdisk use, **+1953525168** .  That is the sector count on your 1TB disks.

Then, you can modify and follow my previous instructions.

---

### Post by blackstripes on 2012-07-06
Okay, I think I've got it.  

fdisk /dev/sdf:

```
root@pzwolinski-EP45-UD3L:~# fdisk /dev/sdf

The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (7-3907029167, default 7): 2048
Last sector, +sectors or +size{K,M,G} (2048-3907029167, default 3907029167): +1953525168

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 2
First sector (7-3907029167, default 7): 
Using default value 7
Last sector, +sectors or +size{K,M,G} (7-2047, default 2047): 
Using default value 2047

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
```

fdisk -l:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   781422767   390711383+  ee  GPT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000467ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108271615    54134784   83  Linux
/dev/sdb2       108273662   125044735     8385537    5  Extended
/dev/sdb5       108273664   125044735     8385536   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  1953525167   976762583+  fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders, total 3907045376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x000c260e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  1953527216   976762584+  fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.
/dev/sdf2               7        2047        1020+  83  Linux

Partition table entries are not in disk order

```

...but I noticed this message in disk utility.  Is this safe to ignore? 
[IMG]https://dl.dropbox.com/u/35008053/Screenshot%20from%202012-07-06%2009%3A06%3A51.png[/IMG]

---

### Post by blackstripes on 2012-07-06
Also, would it be a better idea to create the filesystem on my 2nd partition prior to adding it to the array, just to err on the side of caution?

---

### Post by blackstripes on 2012-07-06
Hah! Progress! :guitar:

I was following your example where the default first sector was 2048 for partition 1, but in my case the default is 7.  I tried using 7 in lieu of 2048 and now my disk isn't misaligned (I don't think it is anyway).  

fdisk /dev/sdf:

```
The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (7-3907029167, default 7): 7 
Last sector, +sectors or +size{K,M,G} (7-3907029167, default 3907029167): +1953525168

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 2
First sector (1953525176-3907029167, default 1953525759): 
Using default value 1953525759
Last sector, +sectors or +size{K,M,G} (1953525759-3907029167, default 3907029167): 
Using default value 3907029167

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

fdisk -l:

```


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   781422767   390711383+  ee  GPT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000467ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108271615    54134784   83  Linux
/dev/sdb2       108273662   125044735     8385537    5  Extended
/dev/sdb5       108273664   125044735     8385536   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  1953525167   976762583+  fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders, total 3907045376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x00012000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               7  1953525175   976762584+  fd  Linux raid autodetect
/dev/sdf2      1953525759  3907029167   976751704+  83  Linux
```

So, this looks pretty good, no?  One thing I don't understand is in the fdisk -l output - why is the /dev/sdf1 partion 1 block larger than my /dev/sdc, /dev/sdd, and /dev/sde?

---

### Post by rubylaser on 2012-07-06
> **blackstripes said:**
> Also, would it be a better idea to create the filesystem on my 2nd partition prior to adding it to the array, just to err on the side of caution?

That partitioning looks good, except it is an advanced format drive, so the partition is not properly aligned. This may have a performance impact, but shouldn't be a big deal in terms of usability.  You can add the filesystem to the second partition at any point.  mdadm will only write the superblock information to the partition that is added to the array.

---

### Post by rubylaser on 2012-07-06
> **blackstripes said:**
> Hah! Progress! :guitar:

I was following your example where the default first sector was 2048 for partition 1, but in my case the default is 7.  I tried using 7 in lieu of 2048 and now my disk isn't misaligned (I don't think it is anyway).  

fdisk /dev/sdf:

```
The device presents a logical sector size that is smaller than
the physical sector size. Aligning to a physical sector (or optimal
I/O) size boundary is recommended, or performance may be impacted.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (7-3907029167, default 7): 7 
Last sector, +sectors or +size{K,M,G} (7-3907029167, default 3907029167): +1953525168

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 2): 2
First sector (1953525176-3907029167, default 1953525759): 
Using default value 1953525759
Last sector, +sectors or +size{K,M,G} (1953525759-3907029167, default 3907029167): 
Using default value 3907029167

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 83

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```

fdisk -l:

```


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   781422767   390711383+  ee  GPT

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000467ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   108271615    54134784   83  Linux
/dev/sdb2       108273662   125044735     8385537    5  Extended
/dev/sdb5       108273664   125044735     8385536   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  1953525167   976762583+  fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000407232512 bytes
2 heads, 4 sectors/track, 488380672 cylinders, total 3907045376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 3584 bytes
Disk identifier: 0x00012000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               7  1953525175   976762584+  fd  Linux raid autodetect
/dev/sdf2      1953525759  3907029167   976751704+  83  Linux
```

So, this looks pretty good, no?  One thing I don't understand is in the fdisk -l output - why is the /dev/sdf1 partion 1 block larger than my /dev/sdc, /dev/sdd, and /dev/sde?

I'm not sure why it's off by 1 because you did everything correct.  The good news is that it won't matter because mdadm will use the smallest sector size on all of your disks to determine the array size.  So /dev/sdf1 will have 1 sector that goes unused :)

---

### Post by blackstripes on 2012-07-06
Okay, time to move forward with the scary part!

---

### Post by rubylaser on 2012-07-06
You'll be fine :)  Just take your time and make sure you get your commands correct before proceeding.

---

### Post by blackstripes on 2012-07-06
Alright done for now! Just ran these lines:

```

mdadm --add /dev/md0 /dev/sdf1
```

```

mdadm --grow /dev/md0 --raid-devices=4
```

```
watch cat /proc/mdstat
```

...and I'm now watching the process:

```
Every 2.0s: cat /proc/mdstat                           Fri Jul  6 10:31:57 2012

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [r
aid10]
md0 : active raid5 sdf1[4] sde[3] sdc[0] sdd[1]
      1953522688 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  0.7% (6929412/976761344) finish=640.3
min speed=25241K/sec

unused devices: <none> 
```

Time go do something else for a while!  

Thanks much for your help rubylaser and good luck with your Ubuntu Membership - you sure know your stuff!

---

### Post by rubylaser on 2012-07-06
> **blackstripes said:**
> Alright done for now! Just ran these lines:

```

mdadm --add /dev/md0 /dev/sdf1
```

```

mdadm --grow /dev/md0 --raid-devices=4
```

```
watch cat /proc/mdstat
```

...and I'm now watching the process:

```
Every 2.0s: cat /proc/mdstat                           Fri Jul  6 10:31:57 2012

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [r
aid10]
md0 : active raid5 sdf1[4] sde[3] sdc[0] sdd[1]
      1953522688 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      [>....................]  reshape =  0.7% (6929412/976761344) finish=640.3
min speed=25241K/sec

unused devices: <none> 
```

Time go do something else for a while!  

Thanks much for your help rubylaser and good luck with your Ubuntu Membership - you sure know your stuff!

Thanks:)  Please let me know how this turns out for you.

---

### Post by blackstripes on 2012-07-06
Will do... still reshaping. :)

Regarding this command:

```
fsck.ext4 /storage
```

My filesystem is Ext3, so I'm assuming I would actually want to run this?

```
fsck.ext3 /storage
```

(where /storage = mount point)

---

### Post by rubylaser on 2012-07-06
> **blackstripes said:**
> Will do... still reshaping. :)

Regarding this command:

```
fsck.ext4 /storage
```

My filesystem is Ext3, so I'm assuming I would actually want to run this?

```
fsck.ext3 /storage
```

(where /storage = mount point)

You'd want to unmount your array, and then run the fsck.ext3
```
umount /storage
fsck.ext3 /dev/md0
```

---

### Post by blackstripes on 2012-07-06
The reshaping is finished and I moved on to checking the file system.  Ubuntu was complaining that something else was using the array and it wouldn't let me umount the array, so I moved on to expanding the file system and will fsck after a restart (hope that is okay...)

The resize2fs command is taking a while but found I can watch the process by running this:

```
watch -n3 df
```

...currently:

```
Every 3.0s: df                                          Fri Jul  6 21:46:13 2012

Filesystem      1K-blocks       Used Available Use% Mounted on
/dev/sdb1        54025876   14494192  36824948  29% /
udev              4128436          4   4128432   1% /dev
tmpfs             1654364       1248   1653116   1% /run
none                 5120          0      5120   0% /run/lock
none              4135908      20956   4114952   1% /run/shm
/dev/md0       2061794616 1824757748 132310784  94% /media/Movies
```

Lookin' good so far.  ;)

---

### Post by blackstripes on 2012-07-06
While I'm waiting on the resize I ran:

```
sudo mkfs.ext4 /dev/sdf2

```

```
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
61054976 inodes, 244187926 blocks
12209396 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done     

```

---

### Post by rubylaser on 2012-07-06
Looks good :)

---

### Post by blackstripes on 2012-07-06
SUCCESS!

```
/dev/md0:
        Version : 1.2
  Creation Time : Sun Apr 29 20:04:55 2012
     Raid Level : raid5
     Array Size : 2930284032 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976761344 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Fri Jul  6 22:50:49 2012
          State : active 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : fileserver:0
           UUID : ccfd3103:c2db2111:129b52e1:6d5b8fc3
         Events : 4034

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       3       8       64        2      active sync   /dev/sde
       4       8       81        3      active sync   /dev/sdf1

```

Many thanks for your help! 8)

---

### Post by rubylaser on 2012-07-07
No problem.  Glad you got it working.  Please mark the thread as solved under the Thread Tools at the top.

---

