---
title: "Server Raid"
date: 2015-09-16
forum: Server Platforms
---

### Post by mobo on 2015-09-16
I have been running an Ubuntu Media Server for a couple of years and I think I may now have a n issue but am really unsure how to diagnose and repair.

In Webmin I found this under "Linux Raid" 

/dev/md0 	active, degraded 	RAID1 (Mirrored) 	13.96 GB 	/dev/sda1
/dev/md1 		                                          1.86 GB 	
/dev/md2 	clean, degraded 	RAID1 (Mirrored) 	915.55 GB 	/dev/sda6

There are two 1 Terrabyte drives in this particular computer in Raid 1. From looking at the above can anyone tell what is wrong and how to diagnose further ...Please and thanks

---

### Post by darkod on 2015-09-16
1. Forget webmin.

2. Log in with standard ssh session (you can do that right?), and post the output of this command:
```
cat /proc/mdstat
```

That will give basic stats about mdadm. After that we will see.

---

### Post by mobo on 2015-09-16
Here is the result..And thanks for responding

# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0]
      14638976 blocks super 1.2 [2/1] [U_]

md2 : active raid1 sda6[0]
      960028480 blocks super 1.2 [2/1] [U_]

md1 : inactive sda5[0](S)
      1950720 blocks super 1.2

---

### Post by darkod on 2015-09-16
It looks like one disk is gone, probably it was /dev/sdb. Only /dev/sda remains.

Do you know if you were using md1 for anything? That is inactive array now.

Can you also post:
```
cat /etc/fstab
sudo parted /dev/sda print all
```

---

### Post by mobo on 2015-09-16
I dont recall using something specific like an "md1" but I did create md device then used raid 1..

****************

```
charlie@Server1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md125 during installation
UUID=bd4257e2-7b99-44d6-ad41-3d98c244ee52 /               ext4    errors=remount-ro 0       1
# /media/files was on /dev/md127 during installation
UUID=e80f9b6a-f15a-44d9-a54f-295228e92998 /media/files    ext4    defaults        0       2
# swap was on /dev/md126 during installation
UUID=3a75ede8-cf7c-443e-8451-a8c52b08ae69 none            swap    sw              0       0
```

```
charlie@Server1:~$ sudo parted /dev/sda print all
[sudo] password for charlie:
Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary   ntfs         boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical                raid
 6      17.0GB  1000GB  983GB   logical                raid


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary                boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical   ext4         raid
 6      17.0GB  1000GB  983GB   logical   ext4         raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 15.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  15.0GB  15.0GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 983GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  983GB  983GB  ext4
```

---

### Post by darkod on 2015-09-16
Hmmm, you had a third array it seems, md1, and that was swap. Right now it's inactive but since the system can function without swap I think that is why you didn't even notice it failed.

The sdb disk is reported by parted together with its partitions, but it's not in the raid any more. Lets see more details of the raid data...

```
sudo mdadm --detail /dev/md0
sudo mdadm --detail /dev/md2
sudo mdadm --examine /dev/sd[ab]1
sudo mdadm --examine /dev/sd[ab]6
```

When posting the output please post it in CODE tags, it helps keep the formatting and read it easier.

---

### Post by mobo on 2015-09-16
sudo mdadm --detail /dev/md0

    ```
 Version : 1.2
  Creation Time : Fri Jun 28 16:34:01 2013
     Raid Level : raid1
     Array Size : 14638976 (13.96 GiB 14.99 GB)
  Used Dev Size : 14638976 (13.96 GiB 14.99 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Wed Sep 16 16:52:27 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : server2:0
           UUID : 8a05d97d:72df34e1:f462ad65:b4925eb9
         Events : 1545738

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
```

sudo mdadm --detail /dev/md2

```
        Version : 1.2
  Creation Time : Fri Jun 28 16:34:17 2013
     Raid Level : raid1
     Array Size : 960028480 (915.55 GiB 983.07 GB)
  Used Dev Size : 960028480 (915.55 GiB 983.07 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Wed Sep 16 16:21:39 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : server2:2
           UUID : fb7ff047:d519f888:d4aaf4f9:ae3f45fb
         Events : 6308

    Number   Major   Minor   RaidDevice State
       0       8        6        0      active sync   /dev/sda6
       1       0        0        1      removed
```


sudo mdadm --examine /dev/sd[ab]1

        ```
  Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8a05d97d:72df34e1:f462ad65:b4925eb9
           Name : server2:0
  Creation Time : Fri Jun 28 16:34:01 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 29278208 (13.96 GiB 14.99 GB)
     Array Size : 14638976 (13.96 GiB 14.99 GB)
  Used Dev Size : 29277952 (13.96 GiB 14.99 GB)
    Data Offset : 16384 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f67a6e41:4737922d:073311a4:ca6b6bfa

    Update Time : Wed Sep 16 16:54:57 2015
       Checksum : 90835692 - correct
         Events : 1545806


   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdb1.



```


sudo mdadm --examine /dev/sd[ab]6
```

          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : fb7ff047:d519f888:d4aaf4f9:ae3f45fb
           Name : server2:2
  Creation Time : Fri Jun 28 16:34:17 2013
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1920057344 (915.55 GiB 983.07 GB)
     Array Size : 960028480 (915.55 GiB 983.07 GB)
  Used Dev Size : 1920056960 (915.55 GiB 983.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 7f132391:b6f3053e:d883b7fd:8f68022d

    Update Time : Wed Sep 16 16:21:39 2015
       Checksum : a643dce9 - correct
         Events : 6308


   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)
/dev/sdb6:
   MBR Magic : aa55
Partition[0] :   1920317440 sectors at         2048 (type fd)
```

---

### Post by darkod on 2015-09-16
OK. As you can see yourself, the second device from md0 and md2 has somehow been removed. Further more, sdb1 does not contain mdadm superblock and sdb6 has a superblock but no useful info in it.

First lets remove the sdb6 superblock and then add sdb1 to md0.
```
sudo mdadm --zero-superblock /dev/sdb6
sudo mdadm /dev/md0 --add /dev/sdb1
```

If that goes well, md0 should start syncing sdb1. You can confirm that by cat /proc/mdstat. It should be rebuilding the array. If that is well, and finishes correctly, add sdb6 to md2 after that.
```
sudo mdadm /dev/md2 --add /dev/sdb6
```

Again, monitor it if it's syncing and when it finishes.

---

### Post by mobo on 2015-09-16
```
 sudo mdadm --zero-superblock /dev/sdb6
mdadm: Unrecognised md component device - /dev/sdb6
# sudo mdadm /dev/md0 --add /dev/sdb1
mdadm: add new device failed for /dev/sdb1 as 2: Invalid argument
```
#

---

### Post by darkod on 2015-09-16
Weird... Lets use verbose to get more info while adding:
```
sudo mdadm --verbose /dev/md0 --add /dev/sdb1
```

---

### Post by mobo on 2015-09-16
Similar result:
```


mdadm: add new device failed for /dev/sdb1 as 2: Invalid argument
```

---

### Post by darkod on 2015-09-16
Hmmm, there might be something wrong with disk sdb after all. The partition table shows up and the partitions, but that is not proof all is good.

It might be best to check the disk with smartmontools. You have instructions here for example: [https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl](https://www.thomas-krenn.com/en/wiki/SMART_tests_with_smartctl)

You need to run it on /dev/sdb. Probably the long test is best, but use the command to check the approx time first, that will tell you how long it will run the test. See if that fineds anything.

Other option, with or without smart test, is to delete all partitions on /dev/sdb and recreate them again. Then try to add them to the arrays. If you wanna try that...

---

### Post by mobo on 2015-09-16
Ill try the first option first..Thanks

---

### Post by mobo on 2015-09-16
Hey..Thanks a million for your assistance. In the end I pulled the drive and tested it and it has many many errors..I couldn't even low level format it...I will be replacing the drive with a new drive so in regards to creating the new drives partitions and mirroring the drive I have a little info here. Can you look at it to see if it correct?

Adding The New Hard Disk
Run

sfdisk -d /dev/sda | sfdisk /dev/sdb

Then

cat /proc/mdstat

---

### Post by darkod on 2015-09-17
The sfdisk is usually used as a quick way to copy the partition table layout from one disk to another. Personally I don't use it, I create the partitions manually. But the sfdisk should work just fine.

After that, you are missing one step. You need to add sdb1 and sdb6 partitions to their respective arrays. After each add, monitor the status with cat /proc/mdstat:
```
sudo mdadm /dev/md0 --add /dev/sdb1
sudo mdadm /dev/md2 --add /dev/sdb6
```

About md1 and the swap, we haven't dealt with it so far because it is not very important. The root array and the data array are much more important. After md0 and md2 are successfully configured we will do md1 at the end.

---

### Post by mobo on 2015-09-21
Managed to get another identical drive today so here goes..Do I need to remove the old drive first in mdadm?

---

### Post by darkod on 2015-09-22
In your case, you can simply disconnect the disk physically. In the --detail output you did you can see the second member of mdadm is already removed in all arrays.

In general, yes, to physically remove a disk with partitions that are members of mdadm, you have to first "mark" those partitions as Fail and then as Removed in mdadm. Only then you should disconnect the disk.

---

### Post by mobo on 2015-09-22
It seemed to go well but then I saw this:
```

md1 : inactive sda5[0](S)
      1950720 blocks super 1.2

md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

---

### Post by darkod on 2015-09-22
What is the problem? Both md0 and md2 are active with two members. md1 is the swap and we left it for the end to sort it out.

The md1 inactive is confusing you?

---

### Post by mobo on 2015-09-22
Just the fact that it was inactive is what i am confused about. Do I not need that swap raid?

---

### Post by darkod on 2015-09-22
Yes and no. First, the role of swap in linux is of virtual RAM. If it runs out of RAM (too much stuff to do), it starts using swap. If you have sufficient RAM it will probably never need swap.

Also, for swap you can easily set both partitions from the two disks to be used in swap but without actually raiding them. That's what I have on my home server. Four disks, four swap partitions, but not raided. In /etc/fstab you make swap entries for all four partitions and that's it. I can help you with the syntax when i get home if you want.

In such case you will need to clear the remains of that md1 array and that's it, you're good to go...

Or you can create new md1 and use that as swap in fstab (I believe you still have an entry for the old md1 in there).

Those are your options...

---

### Post by mobo on 2015-09-22
I would live to be walked through the process. I am in and out for most of the day here as well. Its winterize the pool day for me today......But please yes lets see what we can do with it in whatever you think is best.

---

### Post by darkod on 2015-09-22
OK, I will take a look when at home. Meanwhile please post current output of:
```
sudo parted -l
cat /etc/fstab
cat /etc/mdadm/mdadm.conf
```

---

### Post by mobo on 2015-09-22
sudo parted -l

```
Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary   ntfs         boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical                raid
 6      17.0GB  1000GB  983GB   logical                raid


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary                boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical                raid
 6      17.0GB  1000GB  983GB   logical                raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 15.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  15.0GB  15.0GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md2: 983GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  983GB  983GB  ext4

```

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md125 during installation
UUID=bd4257e2-7b99-44d6-ad41-3d98c244ee52 /               ext4    errors=remount-ro 0       1
# /media/files was on /dev/md127 during installation
UUID=e80f9b6a-f15a-44d9-a54f-295228e92998 /media/files    ext4    defaults        0       2
# swap was on /dev/md126 during installation
UUID=3a75ede8-cf7c-443e-8451-a8c52b08ae69 none            swap    sw              0       0

```

cat /etc/mdadm/mdadm.conf
```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=37c0fd96:e4d856dc:7b8dc605:32873d04 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$

```

---

### Post by darkod on 2015-09-22
I think you better have swap configured as raid1 too, if this is important/production server. Usually it doesn't matter much if disk fails and you lose swap but sometimes it can corrupt data.

So, because the old md1 seems inactive and it has no data on it (it was used as swap), best to simply recreate new md1 from sda5 and sdb5. Lets try to clear any traces of the old one first:
```
sudo -i
mdadm /dev/md1 --remove /dev/sda5
mdadm --zero-superblock /dev/sda5
mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sda5 /dev/sdb5
```

After that format md1 for swap and check its UUID string:
```
mkswap /dev/md1
blkid
```

Open /etc/fstab and replace the old swap UUID with the new one. You should be able to activate swap without rebooting:
```
swapon -a
```

That should be it. If that works you will need to add ARRAY definition to mdadm.conf otherwise md1 will not be reassembled at reboot. And delete the old ARRAY definition. But we'll get to that later. First it's important if the above works well.

---

### Post by mobo on 2015-09-22
The first two commands are in error so I stopped

```
root@Server1:~# mdadm /dev/md1 --remove /dev/sda5
mdadm: cannot get array info for /dev/md1
root@Server1:~# mdadm --zero-superblock /dev/sda5
mdadm: Couldn't open /dev/sda5 for write - not zeroing

```

---

### Post by darkod on 2015-09-23
Hmmm, I wasn't sure if the same device name md1 will work, but it was worth a try. Lets try to completely stop md1 first although that shouldn't be necessary because the array is inactive. And to disable all swap in case sda5 is somehow used as swap. Try this before trying to create md1 again.
```
swapoff -a
mdadm --stop /dev/md1
```

After the above try running the same commands to remove sda5 from md1. If it gives you same error, go to the --create command but try creating it as new array /dev/md3, just forget about /dev/md1.

---

### Post by mobo on 2015-09-23
mdadm /dev/md1 --remove /dev/sda5
```
mdadm: error opening /dev/md1: No such file or directory
```


mdadm --create /dev/md1 --level=1 --raid-devices=2 /dev/sda5 /dev/sdb5
```
mdadm: /dev/sda5 appears to be part of a raid array:
    level=raid1 devices=2 ctime=Fri Jun 28 16:34:11 2013
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
Continue creating array?
Continue creating array? (y/n) y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.
```

cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[2]
      14638976 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sda6[0] sdb6[2]
      960028480 blocks super 1.2 [2/2] [UU]

unused devices: <none>

```

---

### Post by darkod on 2015-09-23
OK, that looks good. Now continue with the commands from above. Use the blkid to find the md1 UUID and replace the swap entry UUID string in fstab with the new one. Then try the swapon -a.

---

### Post by mobo on 2015-09-23
blkid```

/dev/sda1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="f67a6e41-4737-922d-0733-11a4ca6b6bfa" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sda5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="8359b9cc-3478-94ea-62a5-b8e97cd034cb" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sda6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="7f132391-b6f3-053e-d883-b7fd8f68022d" LABEL="server2:2" TYPE="linux_raid_member"
/dev/sdb1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="1a9e7d76-f074-3335-9f70-19f722b30a01" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sdb6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="21ea236e-2b66-fe4e-4f32-7b6546acda56" LABEL="server2:2" TYPE="linux_raid_member"
/dev/md2: UUID="e80f9b6a-f15a-44d9-a54f-295228e92998" TYPE="ext4"
/dev/md0: UUID="bd4257e2-7b99-44d6-ad41-3d98c244ee52" TYPE="ext4"
/dev/sdb5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="01cd9337-b1bf-6750-2523-16cdafd809d8" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/md1: UUID="3a75ede8-cf7c-443e-8451-a8c52b08ae69" TYPE="swap"

```

so this is the id i need to use right?   3a75ede8-cf7c-443e-8451-a8c52b08ae69

---

### Post by mobo on 2015-09-23
It is identical to what is already in fstab

---

### Post by mobo on 2015-09-23
Here is how things look as of now:

sudo parted -l

```

Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary   ntfs         boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical                raid
 6      17.0GB  1000GB  983GB   logical                raid


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  15.0GB  15.0GB  primary                boot, raid
 2      15.0GB  1000GB  985GB   extended
 5      15.0GB  17.0GB  1999MB  logical                raid
 6      17.0GB  1000GB  983GB   logical                raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 15.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  15.0GB  15.0GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md1: 1997MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1997MB  1997MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md2: 983GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  983GB  983GB  ext4


```

cat /etc/fstab


```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md125 during installation
UUID=bd4257e2-7b99-44d6-ad41-3d98c244ee52 /               ext4    errors=remount-ro 0       1
# /media/files was on /dev/md127 during installation
UUID=e80f9b6a-f15a-44d9-a54f-295228e92998 /media/files    ext4    defaults        0       2
# swap was on /dev/md126 during installation
UUID=3a75ede8-cf7c-443e-8451-a8c52b08ae69 none            swap    sw              0       0

```


cat /etc/mdadm/mdadm.conf
```


# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=37c0fd96:e4d856dc:7b8dc605:32873d04 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$
```

---

### Post by darkod on 2015-09-23
You probably didn't run the mkswap so it didn't reformat it again as swap. In that case the UUID remained the same. But if it works, leave it. No need to edit fstab right now.

From what I see you will probably need to edit mdadm.conf because the UUID in it for md1 does not correspond to sda5 and sdb5 UUIDs. If you look at the blkid output for sda5 and sdb5, they first have like "common" UUID (identical), and then as a sub-device they have different ones. This first UUID in the line is the UUID that needs to be used in the ARRAY definition in mdadm.conf. You need to do that so that the array gets assembled correctly on boot.

---

### Post by mobo on 2015-09-23
Ok, to be certain I understand...

Take the udid from the fstab above and enter that in mdadm.conf in the place of the md1's udid?

---

### Post by mobo on 2015-09-23
Ok. I got the mdadm.conf to match the sda5 and db5 udid. However the blikid still remains as the old one.

---

### Post by darkod on 2015-09-23
blkid output will stay the same, you are not changing any UUID of any device. Just puting the correct one into mdadm.conf so that it knows which partitions to use when assembling md1 at boot. In this case sda5 and sdb5. It finds them by UUID.

And to answer the previous post, no, you should not copy the fstab UUID into mdadm.conf. But you already figured that out I think.

In /etc/fstab you put the filesystem UUID (whether it's partition, lvm or raid) while in mdadm.conf you put the UUID assigned/created by mdadm so it knows which partitions to combine assembling the md raid arrays.

That's why there is one UUID for md1 swap filesystem, and completely different "shared" UUID on both sda5 and sdb5. One goes in fstab and the other in mdadm.conf. The UUID_SUB are not much relevant for mdadm.

---

### Post by mobo on 2015-09-23
Ok. The udid makes sense to me now...Here is the latest output

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active (auto-read-only) raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

---

### Post by darkod on 2015-09-23
Yes. The md1 has renamed itself in md127 but that also happens sometimes. But it shouldn't say "auto read-only". Did you reboot once? Did everything boot normally and the arrays assembled good?

---

### Post by mobo on 2015-09-23
I just rebooted and its the same as the last one.
cat /etc/mdadm/mdadm.conf
```

# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=b2e96d72-2f85-ad85-b703-84422e68be61 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$
```
 cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active (auto-read-only) raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

blkid
```
/dev/sdb1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="1a9e7d76-f074-3335-9f70-19f722b30a01" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sdb5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="01cd9337-b1bf-6750-2523-16cdafd809d8" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sdb6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="21ea236e-2b66-fe4e-4f32-7b6546acda56" LABEL="server2:2" TYPE="linux_raid_member"
/dev/sda1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="f67a6e41-4737-922d-0733-11a4ca6b6bfa" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sda5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="8359b9cc-3478-94ea-62a5-b8e97cd034cb" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sda6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="7f132391-b6f3-053e-d883-b7fd8f68022d" LABEL="server2:2" TYPE="linux_raid_member"
/dev/md0: UUID="bd4257e2-7b99-44d6-ad41-3d98c244ee52" TYPE="ext4"
/dev/md2: UUID="e80f9b6a-f15a-44d9-a54f-295228e92998" TYPE="ext4"
/dev/md127: UUID="3a75ede8-cf7c-443e-8451-a8c52b08ae69" TYPE="swap"
```

---

### Post by darkod on 2015-09-23
I had similar case of md renaming itself recently. I read somewhere in mdadm.conf in the ARRAY definition to leave just the md device name (like /dev/md1, not like the default syntax of /dev/md/1) and the UUID. It said you don't need the name or metadata parameters. I did that, and after that the array was always with the correct name.

Also, I'm not sure if you need to update-iniramfs after creating the md1. You can give it a shot.

Modify mdadm.conf as I explained just now, if you want to, and then do the:
```
sudo update-initramfs -u
```

See if that helps to have md1 after reboot. And without the read-only part. I don't know why that is there.

PS. In any case the important arrays are good. This is the swap playing up with you. Even if you completely destroy the array and redo it, no big deal.

---

### Post by mobo on 2015-09-23
I think I got it..

swapoff /dev/md127
mkswap /dev/md127
swapon /dev/md127

then ran cat /proc/mdstat and got this
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

---

### Post by darkod on 2015-09-23
I had suggested mkswap after creating the array earlier. But now after the mkswap the filesystem UUID should be different. Check it with blkid and change it in fstab.

---

### Post by mobo on 2015-09-23
sudo update-initramfs -u
```
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
W: mdadm: the array /dev/md/Server1:1 with UUID b2e96d72:2f85ad85:b7038442:2e68be61
W: mdadm: is currently active, but it is not listed in mdadm.conf. if
W: mdadm: it is needed for boot, then YOUR SYSTEM IS NOW UNBOOTABLE!
W: mdadm: please inspect the output of /usr/share/mdadm/mkconf, compare
W: mdadm: it to /etc/mdadm/mdadm.conf, and make the necessary changes.

```

---

### Post by mobo on 2015-09-23
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays


``````
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=b2e96d72-2f85-ad85-b703-84422e68be61 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$
```
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

unused devices: <none>
```

---

### Post by darkod on 2015-09-23
1. I was referring to the md1 swap UUID which will not be the same after the formatting you did with mkswap. You need to adjust that in fstab if you want it to mount at boot. Run blkid and check.

2. I have no idea why update-initramfs gives that message because the md1 UUID is included correctly into mdadm.conf. What is the first CODE section from, the one showing mdadm.conf without any ARRAY definition?

---

### Post by mobo on 2015-09-23
The first one may just have been a copy paste issue..


Here is the new fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md125 during installation
UUID=bd4257e2-7b99-44d6-ad41-3d98c244ee52 /               ext4    errors=remoun$
# /media/files was on /dev/md127 during installation
UUID=e80f9b6a-f15a-44d9-a54f-295228e92998 /media/files    ext4    defaults     $
# swap was on /dev/md126 during installation
UUID=b2e96d72-2f85-ad85-b703-84422e68be61 none            swap    sw           $
```


 /etc/mdadm/mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=b2e96d72-2f85-ad85-b703-84422e68be61 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$

```
blkid
```
/dev/sdb1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="1a9e7d76-f074-3335-9f70-19f722b30a01" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sdb5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="01cd9337-b1bf-6750-2523-16cdafd809d8" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sdb6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="21ea236e-2b66-fe4e-4f32-7b6546acda56" LABEL="server2:2" TYPE="linux_raid_member"
/dev/sda1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="f67a6e41-4737-922d-0733-11a4ca6b6bfa" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sda5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="8359b9cc-3478-94ea-62a5-b8e97cd034cb" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sda6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="7f132391-b6f3-053e-d883-b7fd8f68022d" LABEL="server2:2" TYPE="linux_raid_member"
/dev/md2: UUID="e80f9b6a-f15a-44d9-a54f-295228e92998" TYPE="ext4"
/dev/md0: UUID="bd4257e2-7b99-44d6-ad41-3d98c244ee52" TYPE="ext4"
/dev/md127: UUID="f281cd49-3b5d-4e5f-936a-2875b9b320c7" TYPE="swap"
```

---

### Post by darkod on 2015-09-23
No, no. Remember what we discussed about differences between filesystem UUID and mdadm UUID. The swap UUID is the /dev/md127 UUID f281cd49.... You need that in fstab.

The shared sda5/sdb5 UUID b2e96d72... you need in the ARRAY definition in mdadm.conf (you already have it there).

---

### Post by mobo on 2015-09-23
Thanks for your patience..I guess its a bit to learn on the fly. I made the change then rebooted here are the reports for your review:
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md125 during installation
UUID=bd4257e2-7b99-44d6-ad41-3d98c244ee52 /               ext4    errors=remount-ro 0       1
# /media/files was on /dev/md127 during installation
UUID=e80f9b6a-f15a-44d9-a54f-295228e92998 /media/files    ext4    defaults        0       2
# swap was on /dev/md126 during installation
UUID=f281cd49-3b5d-4e5f-936a-2875b9b320c7 none            swap    sw              0       0
```


blkid
```

/dev/sda1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="f67a6e41-4737-922d-0733-11a4ca6b6bfa" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sda5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="8359b9cc-3478-94ea-62a5-b8e97cd034cb" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sda6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="7f132391-b6f3-053e-d883-b7fd8f68022d" LABEL="server2:2" TYPE="linux_raid_member"
/dev/sdb1: UUID="8a05d97d-72df-34e1-f462-ad65b4925eb9" UUID_SUB="1a9e7d76-f074-3335-9f70-19f722b30a01" LABEL="server2:0" TYPE="linux_raid_member"
/dev/sdb5: UUID="b2e96d72-2f85-ad85-b703-84422e68be61" UUID_SUB="01cd9337-b1bf-6750-2523-16cdafd809d8" LABEL="Server1:1" TYPE="linux_raid_member"
/dev/sdb6: UUID="fb7ff047-d519-f888-d4aa-f4f9ae3f45fb" UUID_SUB="21ea236e-2b66-fe4e-4f32-7b6546acda56" LABEL="server2:2" TYPE="linux_raid_member"
/dev/md2: UUID="e80f9b6a-f15a-44d9-a54f-295228e92998" TYPE="ext4"
/dev/md127: UUID="f281cd49-3b5d-4e5f-936a-2875b9b320c7" TYPE="swap"
/dev/md0: UUID="bd4257e2-7b99-44d6-ad41-3d98c244ee52" TYPE="ext4"
```


cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

md127 : active (auto-read-only) raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]

md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]

unused devices: <none>


```

cat /etc/mdadm/mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=8a05d97d:72df34e1:f462ad65:b4925eb9 name=server2:0
ARRAY /dev/md/1 metadata=1.2 UUID=b2e96d72-2f85-ad85-b703-84422e68be61 name=server2:1
ARRAY /dev/md/2 metadata=1.2 UUID=fb7ff047:d519f888:d4aaf4f9:ae3f45fb name=server2:2

# This file was auto-generated on Fri, 28 Jun 2013 21:24:31 -0300
# by mkconf $Id$

```

---

### Post by darkod on 2015-09-24
If you noticed the md127 again shows as auto read-only. I wonder if at this stage it's better to delete md1/md127 and simply create new array md3. All of this might be because md1 already existed and it was "recreated".

Does swap mount at all? If you run free -m does it show swap size?

---

### Post by mobo on 2015-09-24
As for the read only. I read somewhere that it stary in that state until the swap is written to. Then it changes. A new one is attached below.

free -m
```
           total       used       free     shared    buffers     cached
Mem:          3275       2938        336          6        221       2009
-/+ buffers/cache:        707       2567
Swap:         1904        0       1904  
```


cat /proc/mdstat```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sdb6[2] sda6[0]
      960028480 blocks super 1.2 [2/2] [UU]
      
md127 : active raid1 sdb5[1] sda5[0]
      1950656 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdb1[2] sda1[0]
      14638976 blocks super 1.2 [2/2] [UU]

```

---

### Post by darkod on 2015-09-24
Ah, didn't know that. Maybe because I have no swap on raid so I have never seen the read-only message. The free -m clearly shows your 2GB of swap and the cat results look good now. So I think it all works good.

If you are happy how it's working, you can mark this as Solved. You do that in Thread Tools above the first post on any page of the thread.

---

### Post by mobo on 2015-09-24
It is working great here. I want to thank you. I had serious c-spine injuries a few years ago and this server helps my children so it really means a lot to me to be able to get this back up and running. I really do appreciate the help and more importantly your patience in dealing with me. I have memory loss from head injuries so your support was much needed.:D Thanks again.

---

