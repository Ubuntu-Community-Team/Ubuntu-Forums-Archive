---
title: "Recover Raid 5 on new OS install"
date: 2015-05-17
forum: Server Platforms
---

### Post by Scott_Hatcher on 2015-05-17
Hey guys,

So I recently upgraded the motherboard and processor on my server that I've been running plex on. Along with it I got a new primary HDD for the Linux install. I transfered 4x 2TB HDDs that I had in Raid 5 and managed to get it to rebuild the raid array on the new install. Here is the raid information below.
```
/dev/md0:
        Version : 1.2
  Creation Time : Tue May  5 20:40:47 2015
     Raid Level : raid5
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sun May 17 10:05:34 2015
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1


         Layout : left-symmetric
     Chunk Size : 512K


 Rebuild Status : 4% complete


           Name : mediaserver:0  (local to host mediaserver)
           UUID : 8066286d:31f9ae5d:afc4eab7:a32fda30
         Events : 132


    Number   Major   Minor   RaidDevice State
       4       8        0        0      spare rebuilding   /dev/sda
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

``` 

So I have two questions. First of all, how can I tell if I lost any data. Its not a huge deal if I did, I just would rather not spend several days re-ripping my movie collection. I assume I need to wait for it to rebuild before I can do anything else. Secondly how do I mount it back to /usr?

I have done some google searching and its just left me more confused than anything. Especially about the UUID and fstab.

Thanks

---

### Post by darkod on 2015-05-17
Rebuilt? Existing raid arrays are recognized and do not need to be rebuilt or synced. Which command did you use exactly?

Plus one thing I see in the info is that you used /dev/sda (the whole disk) as member of the array and for the other three members you used partitions (sdb1, sdc1 and sdd1). Usually you would use partitions as members, and on all disks...

Lets clear that out first, and then we will get to the mounting part. Plus /usr is existing non-empty system folder, did you had the array mounted at /usr? Usually you would choose any custom created empty folder as mount point. Not use a system folder.

---

### Post by Scott_Hatcher on 2015-05-17
Rebuilt might not be the correct word. I used mdadm --assemble --scan and it recreated md0 but it only added 3 out of the 4 drives. So then I used the readd command to replace the sda drive, but now I think I added it wrong. Should I remove /dev/sda and try and readd /dev/sda1? Or has the damage been done?

And yes the original install I had /usr mounted to the raid but I dont really care how it gets mounted at this point.

EDIT:

This is the thread where I found to use the assemble command.
[http://ubuntuforums.org/showthread.php?t=850229](http://ubuntuforums.org/showthread.php?t=850229)

---

### Post by darkod on 2015-05-17
That was the correct command to assemble existing array. Strange that it detected only 3 devices. You can fail remove sda now, and add it as sda1. The small problem is that while doing that the array is missing one member, which for raid5 is the maximum it can lose and continue to work. If while syncing sda1 another disk fails, you will get yourself in trouble. But now you are in the same situation, it's syncing sda right now.

The readd might not work, so you might need to zero the superblock on both sda and sda1, and then add sda1 as "new" member. Of course, make sure the sda1 partition still exists before that. If not, create it.

If you need help with the commands, ask first...

---

### Post by Scott_Hatcher on 2015-05-17
Okay so I failed and removed the drive using
```
mdadm /dev/md0 --fail /dev/sda --remove /dev/sda
```

Removed the superblock and when I try and add sda1 it comes back saying no file or directory. Fdisk -l Does show /dev/sda1 as linux raid autodetect. What am I missing?

And thanks for your help!

EDIT:
I realize now that none of the drives are a md device. I over looked that.

---

### Post by darkod on 2015-05-17
So, do you have it added now or not? What's the status?

---

### Post by Scott_Hatcher on 2015-05-17
No it wont add sda1 just sda. Im tempted to let it do its thing and see if after its done if it shows up as sda1

---

### Post by darkod on 2015-05-17
No, it can't show as sda1 later. If it's added as sda it will stay as sda. The full disk. Can you post the output of:
```
sudo parted -l
sudo mdadm -D /dev/md0
```

---

### Post by Scott_Hatcher on 2015-05-17
parted -l results
```
Model: ATA WDC WD20EURS-73T (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid
 
 
Model: ATA WDC WD20EURS-73T (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid
 
 
Model: ATA WDC WD20EURS-73T (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid
 
 
Model: ATA WDC WD20EURS-73T (scsi)
Disk /dev/sdd: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary               raid
 
 
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sde: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  500MB   499MB   primary  ext4            boot
 3      500MB   4500MB  4000MB  primary  linux-swap(v1)
 2      4500MB  1000GB  996GB   primary  ext4
 
 
Model: Linux Software RAID Array (md)
Disk /dev/md0: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
 
Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4

```

mdadm -D /dev/md0 results
```
/dev/md0:
        Version : 1.2
  Creation Time : Tue May  5 20:40:47 2015
     Raid Level : raid5
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent
 
    Update Time : Sun May 17 12:36:30 2015
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
 
         Layout : left-symmetric
     Chunk Size : 512K
 
           Name : mediaserver:0  (local to host mediaserver)
           UUID : 8066286d:31f9ae5d:afc4eab7:a32fda30
         Events : 172
 
    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```

---

### Post by darkod on 2015-05-17
Well, you do have sda1, that's clear. Any messages when trying to add it? You get more output with --verbose.

```
sudo mdadm /dev/md0 --verbose --add /dev/sda1
```

---

### Post by Scott_Hatcher on 2015-05-17
I get the following:
```
mdadm: add new device failed for /dev/sda1 as 4: Invalid argument
```

I did remove the superblock earlier by using:
```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm --zero-superblock /dev/sda[/FONT][/COLOR]
```

I dont know if that makes any difference

---

### Post by darkod on 2015-05-17
You need to do it for sda1 too if you are trying to add it as completely new device.

```
mdadm --zero-superblock /dev/sda1
mdadm /dev/md0 --verbose --add /dev/sda1
```

---

### Post by Scott_Hatcher on 2015-05-17
When removing the superblock from sda1 it says unrecognized md component device. And I get the same error again when adding it.

---

### Post by darkod on 2015-05-17
Weird... we are running out of options unfortunately. What does examine shows for all partitions:
```
mdadm --examine /dev/sd[abcd]1
```

The last option I guess would be to completely wipe /dev/sda (create new msdos partition table), and a new sda1 partition. Then try to add it to the array.

---

### Post by Scott_Hatcher on 2015-05-17
Heres the results for examine
```
mdadm: No md superblock detected on /dev/sda1.
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8066286d:31f9ae5d:afc4eab7:a32fda30
           Name : mediaserver:0  (local to host mediaserver)
  Creation Time : Tue May  5 20:40:47 2015
     Raid Level : raid5
   Raid Devices : 4
 
 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fee67f7d:18d3a5e1:3ab38c9e:264f4222
 
    Update Time : Sun May 17 12:36:30 2015
       Checksum : f1efdd1 - correct
         Events : 172
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : Active device 1
   Array State : .AAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8066286d:31f9ae5d:afc4eab7:a32fda30
           Name : mediaserver:0  (local to host mediaserver)
  Creation Time : Tue May  5 20:40:47 2015
     Raid Level : raid5
   Raid Devices : 4
 
 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 323d55e3:392f2222:5bf56aaf:5dfea8fa
 
    Update Time : Sun May 17 12:36:30 2015
       Checksum : 9eb5a17f - correct
         Events : 172
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : Active device 2
   Array State : .AAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8066286d:31f9ae5d:afc4eab7:a32fda30
           Name : mediaserver:0  (local to host mediaserver)
  Creation Time : Tue May  5 20:40:47 2015
     Raid Level : raid5
   Raid Devices : 4
 
 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : cbc4c33b:795f7596:47a2c9c0:9549d7fc
 
    Update Time : Sun May 17 12:36:30 2015
       Checksum : 7f04517d - correct
         Events : 172
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : Active device 3
   Array State : .AAA ('A' == active, '.' == missing)

```

And I wouldn't be against wiping the partition. If I could mount the raid with just the 3 drives I could pull off the files off and just completely rebuild the array. Do you think there has been any data loss?

---

### Post by darkod on 2015-05-17
Well with three disks it should work fine right now. Raid5 can work without one member. Try mounting at any location temporarily, for example /mnt.

```
sudo mount /dev/md0 /mnt
ls /mnt
```

It should all be there.

---

### Post by Scott_Hatcher on 2015-05-17
Awesome, its all there and now getting transferred elsewhere. 

To delete and rebuild the array I need to do the following correct? Would I need to delete and re-partition everything or would creating a new array take care of that for me.

```

[COLOR=#93A1A1][FONT=Menlo]mdadm --stop /dev/md0[/FONT][/COLOR][COLOR=#93A1A1][FONT=Menlo]mdadm --remove /dev/md0
mdadm --zero-superblock /dev/sd[bcd]1
mdadm --create --verbose /dev/md0 --level=5 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm --detail --scan >> /etc/mdadm.conf
[/FONT][/COLOR]
```

Then to get it to mount on startup I need to add the UUID to the fstab file with what I want it mounted as. Since I'm only putting media on it could I mount it as /plex?

---

### Post by darkod on 2015-05-18
In the --create you will also need one more option: --raid-devices=4 to tell it how many members you want.

I'm not sure you will need the --detail --scan because I think the --create makes the entry in mdadm.conf. Check the content first before try to add it manually. And the exact location I think is /etc/mdadm/mdadm.conf.

Yes, you can create the empty folder /plex and then use that as mount point for the array. You only create it once at the start of course.

---

### Post by Scott_Hatcher on 2015-05-18
I cant seem to win lol. I cant get it to create a new raid now. I went through and deleted all the partions on /dev/sd[abcd]. /dev/sde is my drive where the OS is installed. After deleting the partitions I make new ones and changed their type back to linux raid. I zeroed superblocks for both /dev/sd[abcd] and /dev/sd[abcd]1. I'd assume at this point its like having brand new hard drives installed. 

Here is the my command to create the new raid:
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sd[abcd]1
```

Here are the results:
```

mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: cunk size defaults to 512K
mdadm: size set to 1953381888K
mdadm: Defaulting to version 1.2 metadata
mdadm: Failed to write metadata to /dev/sdb1

```

I cant find anything on google that is close to this error. Im beginning to get annoyed to say the least.

---

### Post by Scott_Hatcher on 2015-05-18
So I figured it out. I used "dd if=/dev/zero of=/dev/sd*" let that run a little bit on each drive. recreated the partitons and everything is now back to working. Thanks again for your help!

---

