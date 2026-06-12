---
title: "mdadm array won't assemble on boot, assembles manually with device list"
date: 2016-09-23
forum: Server Platforms
---

### Post by pad22 on 2016-09-23
I'm running 14.04 LTS with a 5 drive Software RAID array with 2TB drives.  mdadm, lvm and xfs.  My primary boot device is a 256GB SSD.

Had a power outage, and when the power came back, the system wouldn't boot.  When trying to boot, the following is scrolled on the screen repeatedly so I couldn't get past the boot process:

    ```
    Incrementally starting RAID arrays... 
        mdadm: CREATE user root not found 
        mdadm: CREATE group disk not found
        Incrementally started RAID arrays.
```

There is a bug on launchpad for this ([https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1335642](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1335642)), but there doesn't seem to be a definitive workaround - or at least steps easily repeatable by me.

Booting into recovery mode, lists the following information:

    ```
[ 2.482387] md: bind<sdb1> 
    [ 2.408390] md: bind<sda1> 
    [ 2.438005] md: bind<sdc1> 
    [ 2.986691] Switched to clocksource tsc 
    Incrementally starting RAID arrays... 
    mdadm: CREATE user root not found 
    mdadm: CREATE group disk not found 
    [ 31.755948] md/raid:md0: device sdc1 operational as raid disk 1 
    [ 31.756886] md/raid:md0: device sda1 operational as raid disk 0 
    [ 31.756861] md/raid:md0: device sdb1 operational as raid disk 2 
    [ 31.756115] md/raid:md0: device sdd1 operational as raid disk 3 
    [ 31.756531] md/raid:md0: allocated 0kB 
    [ 31.756647] md/raid:md0: raid level 5 active with 4 out of 5 devices, algorithm 2 
    [ 31.756735] md0: detected capacity change from 0 to 8001591181312
    mdadm: started array /dev/md0
    Incrementally started RAID arrays. 
    [ 31.757933] random: nonblocking pool is initialized 
    [ 31.758184]  md0: unknown partition table 
    [ 31.781641] bio: create slab <bio-1> at 1
    Incrementally starting RAID arrays... 
    mdadm: CREATE user root not found 
    mdadm: CREATE group disk not found 
    Incrementally started RAID arrays. 

```

So, booting into a Live CD, the drives all look ok via SMART data.  If I try to run `mdadm --assemble --scan` I get the following warning:

    ```
mdadm: WARNING /dev/sde1 and /dev/sde appear to have very similar superblocks.
          If they are really different, please --zero the superblock on one
          If they are the same or overlap, please remove one from the
          DEVICE list in mdadm.conf.
```

The array is not assembled.

I captured all of the RAID device info here:

    ```
/dev/sda1:
              Magic : a92b4efc
            Version : 0.90.00
               UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0
    
        Update Time : Tue Aug  2 11:43:38 2016
              State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1af33e59 - correct
             Events : 105212
    
             Layout : left-symmetric
         Chunk Size : 64K
    
          Number   Major   Minor   RaidDevice State
    this     0       8       33        0      active sync   /dev/sdc1
    
       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    /dev/sdb1:
              Magic : a92b4efc
            Version : 0.90.00
               UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0
    
        Update Time : Tue Aug  2 11:43:38 2016
              State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1af33e6d - correct
             Events : 105212
    
             Layout : left-symmetric
         Chunk Size : 64K
    
          Number   Major   Minor   RaidDevice State
    this     2       8       49        2      active sync   /dev/sdd1
    
       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    /dev/sdc1:
              Magic : a92b4efc
            Version : 0.90.00
               UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0
    
        Update Time : Tue Aug  2 11:43:38 2016
              State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1af33e7b - correct
             Events : 105212
    
             Layout : left-symmetric
         Chunk Size : 64K
    
          Number   Major   Minor   RaidDevice State
    this     1       8       65        1      active sync   /dev/sde1
    
       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    /dev/sdd1:
              Magic : a92b4efc
            Version : 0.90.00
               UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0
    
        Update Time : Tue Aug  2 11:43:38 2016
              State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1af33e8f - correct
             Events : 105212
    
             Layout : left-symmetric
         Chunk Size : 64K
    
          Number   Major   Minor   RaidDevice State
    this     3       8       81        3      active sync   /dev/sdf1
    
       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    /dev/sde1:
              Magic : a92b4efc
            Version : 0.90.00
               UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0
    
        Update Time : Tue Aug  2 11:43:38 2016
              State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1af33e41 - correct
             Events : 105212
    
             Layout : left-symmetric
         Chunk Size : 64K
    
          Number   Major   Minor   RaidDevice State
    this     4       8        1        4      active sync   /dev/sda1
    
       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1

```

Original /etc/mdadm/mdadm.conf (nothing crazy):

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
    ARRAY /dev/md0 metadata=0.90 UUID=d5f6a94e:185828ec:b1902148:b8793263
    
    # This file was auto-generated on Wed, 09 May 2012 23:34:51 -0400
    # by mkconf $Id$

```

So, if I run `sudo mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1` (depending on which drives are the raid drives) then the array assembles correctly and I can access the files.

I have tried to pull the power from all of the RAID drives, the system still doesn't boot (same infinite loop).

I have tried to `chroot` and define each device in the array in /etc/mdadm/mdadm.conf and then update initramfs, which is where I am now, and the system still won't boot.

Here is the new `/etc/mdadm/mdadm.conf`:

    ```
# mdadm.conf
    #
    # Please refer to mdadm.conf(5) for information about this file.
    #
    
    # by default (built-in), scan all partitions (/proc/partitions) and all
    # containers for MD superblocks. alternatively, specify devices to scan, using
    # wildcards if desired.
    #DEVICE partitions containers
    DEVICE /dev/sd[abcde]1
    
    # auto-create devices with Debian standard permissions
    CREATE owner=root group=disk mode=0660 auto=yes
    
    # automatically tag new arrays as belonging to the local system
    HOMEHOST <system>
    
    # instruct the monitoring daemon where to send mail alerts
    MAILADDR root
    
    # definitions of existing MD arrays
    #ARRAY /dev/md0 metadata=0.90 UUID=d5f6a94e:185828ec:b1902148:b8793263
    ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
    
    # This file was auto-generated on Wed, 09 May 2012 23:34:51 -0400
    # by mkconf $Id$

```

What I don't understand is what is causing the system not to assemble on boot, when I can assemble manually by specifying the devices.

One of the remaining things that seem odd is that I recorded the boot process on slow-mo camera, and don't see `/dev/sde` or `/dev/sde1` in the boot messages.  I'm going to look into that, but don't really know what to look into.

_****Update - Sat Aug 13****_

I've been doing more investigations.  So, doing a `sudo fdisk -l` shows the following for the drives in the RAID 5:

```
    ubuntu@ubuntu:~$ sudo fdisk -l


    Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
    81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0xca36f687


       Device Boot      Start         End      Blocks   Id  System
    /dev/sda1            2048  3907029167  1953513560   fd  Linux raid autodetect


    WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




    Disk /dev/sdc: 2000.4 GB, 2000398933504 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907029167 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
    Disk identifier: 0x00000000


       Device Boot      Start         End      Blocks   Id  System
    /dev/sdc1               1  3907029166  1953514583   ee  GPT
    Partition 1 does not start on physical sector boundary.


    Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
    81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xf66042a2


       Device Boot      Start         End      Blocks   Id  System
    /dev/sdd1            2048  3907029167  1953513560   fd  Linux raid autodetect


    Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
    81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x2006adb2


       Device Boot      Start         End      Blocks   Id  System
    /dev/sde1            2048  3907029167  1953513560   fd  Linux raid autodetect


    Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
    81 heads, 63 sectors/track, 765633 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disk identifier: 0x0008b3d6


       Device Boot      Start         End      Blocks   Id  System
    /dev/sdf1            2048  3907029167  1953513560   fd  Linux raid autodetect


    Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
    255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xd46f102b


       Device Boot      Start         End      Blocks   Id  System
    /dev/sdg1              64  3907029167  1953514552   fd  Linux raid autodetect

```

So, obviously here `/dev/sdg1` starts at a different sector location than the other RAID partitions.  So, next step was to examine the `/dev/sdg` drive.  As you can see by the following 4 commands, mdadm doesn't examine `/dev/sdg` drive and detect the RAID like it does for the other drives (`/dev/sda` used as an example below).  ***Is this a hint as to what is actually wrong?***

```
    ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdg
    /dev/sdg:
       MBR Magic : aa55
    Partition[0] :   3907029104 sectors at           64 (type fd)
    ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdg1
    /dev/sdg1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0


        Update Time : Sun Aug 14 03:04:59 2016
          State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1b029700 - correct
         Events : 105212


         Layout : left-symmetric
         Chunk Size : 64K


          Number   Major   Minor   RaidDevice State
    this     3       8       81        3      active sync   /dev/sdf1


       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sda
    /dev/sda:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0


        Update Time : Sun Aug 14 03:04:59 2016
          State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1b0296b2 - correct
         Events : 105212


         Layout : left-symmetric
         Chunk Size : 64K


          Number   Major   Minor   RaidDevice State
    this     4       8        1        4      active sync   /dev/sda1


       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1
    ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sda1
    /dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d5f6a94e:185828ec:b1902148:b8793263
      Creation Time : Tue Feb 15 18:47:10 2011
         Raid Level : raid5
      Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
         Array Size : 7814053888 (7452.06 GiB 8001.59 GB)
       Raid Devices : 5
      Total Devices : 5
    Preferred Minor : 0


        Update Time : Sun Aug 14 03:04:59 2016
          State : clean
     Active Devices : 5
    Working Devices : 5
     Failed Devices : 0
      Spare Devices : 0
           Checksum : 1b0296b2 - correct
         Events : 105212


         Layout : left-symmetric
         Chunk Size : 64K


          Number   Major   Minor   RaidDevice State
    this     4       8        1        4      active sync   /dev/sda1


       0     0       8       33        0      active sync   /dev/sdc1
       1     1       8       65        1      active sync   /dev/sde1
       2     2       8       49        2      active sync   /dev/sdd1
       3     3       8       81        3      active sync   /dev/sdf1
       4     4       8        1        4      active sync   /dev/sda1

```

Lastly, I'm confused by running `sudo mdadm --assemble --scan -v` (verbose mode) because it seems to give a warning about the drive (`/dev/sdf`) and the first (and only) partition (`/dev/sdf1`) looking the same and then stop assembling. See here:

    ```
ubuntu@ubuntu:~$ sudo mdadm --assemble --scan -v
    mdadm: looking for devices for /dev/md0
    mdadm: Cannot assemble mbr metadata on /dev/sdh1
    mdadm: Cannot assemble mbr metadata on /dev/sdh
    mdadm: no recogniseable superblock on /dev/sdb5
    mdadm: Cannot assemble mbr metadata on /dev/sdb2
    mdadm: Cannot assemble mbr metadata on /dev/sdb1
    mdadm: Cannot assemble mbr metadata on /dev/sdb
    mdadm: no RAID superblock on /dev/sdg
    mdadm: no RAID superblock on /dev/sdc1
    mdadm: no RAID superblock on /dev/sdc
    mdadm: cannot open device /dev/sr0: No medium found
    mdadm: no RAID superblock on /dev/loop0
    mdadm: no RAID superblock on /dev/ram15
    mdadm: no RAID superblock on /dev/ram14
    mdadm: no RAID superblock on /dev/ram13
    mdadm: no RAID superblock on /dev/ram12
    mdadm: no RAID superblock on /dev/ram11
    mdadm: no RAID superblock on /dev/ram10
    mdadm: no RAID superblock on /dev/ram9
    mdadm: no RAID superblock on /dev/ram8
    mdadm: no RAID superblock on /dev/ram7
    mdadm: no RAID superblock on /dev/ram6
    mdadm: no RAID superblock on /dev/ram5
    mdadm: no RAID superblock on /dev/ram4
    mdadm: no RAID superblock on /dev/ram3
    mdadm: no RAID superblock on /dev/ram2
    mdadm: no RAID superblock on /dev/ram1
    mdadm: no RAID superblock on /dev/ram0
    mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 3.
    mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 1.
    mdadm: /dev/sdf is identified as a member of /dev/md0, slot 1.
    mdadm: WARNING /dev/sdf1 and /dev/sdf appear to have very similar superblocks.
          If they are really different, please --zero the superblock on one
          If they are the same or overlap, please remove one from the
          DEVICE list in mdadm.conf.

```

At this point, I'm wondering what I should do next?

[LIST=1]
[*]Should I remove /dev/sdg1 from the array, reconstruct it to start at sector 2048 and add it back in and let the array reconstruct itself?  If so, what steps should I take?
[*]Is there anything actually wrong with starting at sector 64?  Once I am able to assemble the array from the LIVE CD by specifying the devices to use, is there a way to determine if the '/dev/sdg' drive is working properly in the array?  If so, is it worthwhile doing #1 above, or is there a way to manually set the devices in the array by device identifier, etc.?  Specifying the devices in the mdadm.conf did not work.
[*]Are there other diagnostic steps I should try?
[/LIST]

Thanks in advance for your help!

****Update - Sept 23, 2016****

So, I tried option #1 above on the drive that started at sector 64.  I failed the drive, removed it from the array and repartitioned the space.  I then added it back in and let it rebuild.  I also ran an offline SMART test on the drive.  All passed and the drive was added back into the array without issue.

I don't know what prompted this next step, but I tried selecting a different kernel revision from the grub menu.  Through the advanced boot options, I CANNOT boot from `3.13.0-92-generic` nor can I boot from `3.13.0-86-generic`.  They both go into the infinite loop.

HOWEVER, I can boot off of `3.13.0-63-generic` and it seems like every other kernel older than that (although I have not tested them all).  Obviously, the system is not working 100%: although it takes me to the GUI, I can't login.  I have to switch to a terminal and login that way.  However, the array is mounted and ready to go and Samba is running fine.  

So, my next thought was to look into what was different between the `initrd` images.  I expanded the non-working image and the working image and compared all of the non-binary files and although I'm a rookie, I didn't see anything wrong.

**At this point it seems to be pointing me at a difference between the kernel images, but I'm way out of my depth here and not sure what I should do next.**

**Please help?  Thanks in advance for your help.**

---

### Post by cariboo on 2016-09-24
Moved to Server Platforms, as you may get help quicker here.

---

### Post by darkod on 2016-09-24
There has been a lot going on it seems... Can you shortly confirm what the current status is?

Also, as you can see by fdisk -l, some disks have gpt tables and fdisk does not support that. To be able to see both msdos and gpt disks, use:
```
sudo parted -l
```

To get a printout in sectors (to be able to identically compare partitions on disks), you can do like:
```
sudo parted /dev/sda unit s print
```

That message you had from mdadm about sdf and sdf1 having superblocks, did you ever sort it out? Usually mdadm is best to be used with partitions, not whole disks (even if you have a single partition on the whole disk, that is still a partition, not the disk designator /dev/sdf). So, only /dev/sdf1 should have a superblock and be member of the array, not /dev/sdf. But if at some point you mistakenly added sdf to the array instead of sdf1, be careful about removing the superblock from sdf. First make sure which are the actual array members, and if sdf is not one of them it should be safe to remove the superblock from it:
```
sudo mdadm --zero-superblock /dev/sdf
```

Of course, first check everything and also make sure drive letters haven't shifted around. I am going by what you posted last but if drive letters shifted make sure you are working on the correct disk.

---

### Post by pad22 on 2016-09-28
Apologies - I wasn't subscribed to this thread, so I didn't see these messages.  Thanks for getting back to me.

> **darkod said:**
> There has been a lot going on it seems... Can you shortly confirm what the current status is?


Current status:  I can boot off old kernel images, just not the two most recent images.  

> **darkod said:**
> 
Also, as you can see by fdisk -l, some disks have gpt tables and fdisk does not support that. To be able to see both msdos and gpt disks, use:
```
sudo parted -l
```

To get a printout in sectors (to be able to identically compare partitions on disks), you can do like:
```
sudo parted /dev/sda unit s print
```


```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  3907029167s  3907027120s  primary               raid

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  3907029167s  3907027120s  primary               raid

ubuntu@ubuntu:~$ sudo parted /dev/sdc unit s print
Model: ATA WDC WD20EARX-008 (scsi)
Disk /dev/sdc: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  3907029167s  3907027120s  primary               raid

ubuntu@ubuntu:~$ sudo parted /dev/sdd unit s print
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdd: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  3907029167s  3907027120s  primary               raid

ubuntu@ubuntu:~$ sudo parted /dev/sde unit s print
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sde: 3907029168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End          Size         Type     File system  Flags
 1      2048s  3907029167s  3907027120s  primary               raid

```

Everything here looks OK.  Aligned to 2048 sectors.  All partitions with raid status. 

> **darkod said:**
> 
That message you had from mdadm about sdf and sdf1 having superblocks, did you ever sort it out? Usually mdadm is best to be used with partitions, not whole disks (even if you have a single partition on the whole disk, that is still a partition, not the disk designator /dev/sdf). So, only /dev/sdf1 should have a superblock and be member of the array, not /dev/sdf. But if at some point you mistakenly added sdf to the array instead of sdf1, be careful about removing the superblock from sdf. First make sure which are the actual array members, and if sdf is not one of them it should be safe to remove the superblock from it:
```
sudo mdadm --zero-superblock /dev/sdf
```


I setup all of the drives with partitions and added those to the array.  I was also confused by that message as it appeared when I was trying to assemble by scanning with verbose mode on.  Let's see what happens if I zero the superblocks on the drives and not the partitions.

So, I did this to all of the drives and when I examine the partitions with mdadm I get the following messages:
```

ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sda
ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sdb
ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sdc
ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sdd
ubuntu@ubuntu:~$ sudo mdadm --zero-superblock /dev/sde
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sd[abcde]1 
mdadm: No md superblock detected on /dev/sda1.
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sde1.

```

> **darkod said:**
> 
Of course, first check everything and also make sure drive letters haven't shifted around. I am going by what you posted last but if drive letters shifted make sure you are working on the correct disk.

Yes, I have been very careful to notice that drive letters are changing.  The good thing is that I have everything backed up onto external drives (it takes a long time to backup over 8TB over USB2).  If anything catastrophic happens I have everything backed up.  I also have the details of the array assembly order above should I need to reassemble manually (at least I think I do).

So, with the error messages above about **no md superblocks**, any ideas what I should do next?

---

### Post by darkod on 2016-09-29
Strange, that seems to have removed the SB on the partitions too, even though you used the disk designators. I guess the only thing you can do now is re-create with assume-clean otherwise without SB it won't assemble. You said you remember more or less the order of disks, so use the order you think is correct (mdadm should be smart enough to find the correct order anyway). In my example I will just use sda1-sde1.
```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=5 /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

That should get it going... If there is an array currently assembled you will need to stop it first:
```
sudo mdadm --stop /dev/md0
```

---

