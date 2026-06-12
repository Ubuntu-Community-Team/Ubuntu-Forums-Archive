---
title: "mdadm error when attempting to add a device to RAID 5 array."
date: 2009-10-23
forum: Server Platforms
---

### Post by treilanin on 2009-10-23
Hello,

I currently have a 4x 750GB Hard Drive Raid 5 array running on the server edition of Ubuntu 8.04 (Hardy Heron).  The raid array was originally setup as a 3 x 750GB Raid 5 Array during the initial installation.  About two weeks ago I purchased another 2x 750GB to add to the server and was able to add the first of the two drives /dev/sdd with no issues.

**mdadm version**
```
mdadm - v2.6.3 - 20th August 2007
```[B]

Output of mdadm --examine /dev/md0[/B]
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Apr  1 13:32:59 2008
     Raid Level : raid5
  Used Dev Size : 0
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Oct 23 19:54:36 2009
          State : clean, Not Started
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 35716b21:01565e23:6a8dcb2c:f19c87a7
         Events : 0.487296

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```[B]


cat /proc/mdstat[/B]
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3] sda1[0] sdc1[2] sdb1[1]
      0 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
```When I attempt to add the second 750GB drive /dev/sde to the array I keep getting the following error:

**mdadm /dev/md0 --add /dev/sde1**
```
mdadm: add new device failed for /dev/sde1 as 4: No space left on device
```Searching on the internet for some information on this error message would indicate that somehow this drive is too small to be used in the array.  So based on this information I checked how I partitioned /dev/sde to ensure that it was the same as what I used for /dev/sdd

**fdisk -l /dev/sdd**
```
Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf98fa6a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001   da  Non-FS data
```**fdisk -l /dev/sdw**

```
Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d449f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   da  Non-FS data
```I also checked the output of /proc/partitions to ensure that the block sizes of all the hard drives in my array are the same:

**cat /proc/partitions**
```
major minor  #blocks  name

   8     0  732574584 sda
   8     1  732572001 sda1
   8    16  732574584 sdb
   8    17  732572001 sdb1
   8    32  732574584 sdc
   8    33  732572001 sdc1
   8    48  732574584 sdd
   8    49  732572001 sdd1
   8    64  732574584 sde
   8    65  732572001 sde1
...
```So everything seems to match properly here, which leaves me at a loss for a reason why the drive can't be added to the array.  Does anyone have any idea what I could be doing wrong... or at least maybe something to check?

THanks.

---

### Post by djamu on 2009-10-24
Hi,
a wild guess here ( I assume these drives are the same brand ? )

you did partition the new drives prior the attempt to attach them, so my guess is that somehow the partition has an offset ( but still rounds to blocks > which is normal ) might be that the first partition starts at a different sector

did you use the same partitioning tool?  > check that the partition effectively starts at the same sector ( and block )
( for example if you used fdisk for the initial partitioning and then later used cfdisk for the new ones it might round different ) ..

---

### Post by treilanin on 2009-10-24
Thanks for the reply Djamu.

Yes alll of the drives are Seagate Barracudas with 32MB Cache.  THe original 3 drives are 7200.11 drives (SDA, SDB, SDC) and the two new drives that I purchased are 7200.12 drives (SDD, SDE).  At first I thought the cause was the two drives were different but the SDD drive added with no problems at all.

As for the tool I used, I used fdisk for all of the drives and just used to cylinder defaults during the partition creation process to use the entire drive.  I know fdisk shows that the partitions start and end on the same cylinder which was in my original post.  Here is the sfdisk output for /dev/sdd (part of the array) and /dev/sde (not part of the array)
[B]
sfdisk --list -uS /dev/sdd[/B]
```
Disk /dev/sdd: 91201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdd1            63 1465144064 1465144002  da  Non-FS data
/dev/sdd2             0         -          0   0  Empty
/dev/sdd3             0         -          0   0  Empty
/dev/sdd4             0         -          0   0  Empty
```
**sfdisk --list -uS /dev/sde**
```
Disk /dev/sde: 91201 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sde1            63 1465144064 1465144002  da  Non-FS data
/dev/sde2             0         -          0   0  Empty
/dev/sde3             0         -          0   0  Empty
/dev/sde4             0         -          0   0  Empty
```**sfdisk --list -uB /dev/sdd**
```
Disk /dev/sdd: 91201 cylinders, 255 heads, 63 sectors/track
Units = blocks of 1024 bytes, counting from 0

   Device Boot   Start       End    #blocks   Id  System
/dev/sdd1           31+ 732572032- 732572001   da  Non-FS data
/dev/sdd2            0         -          0    0  Empty
/dev/sdd3            0         -          0    0  Empty
/dev/sdd4            0         -          0    0  Empty
```**sfdisk --list -uB /dev/sde**
```
Disk /dev/sde: 91201 cylinders, 255 heads, 63 sectors/track
Units = blocks of 1024 bytes, counting from 0

   Device Boot   Start       End    #blocks   Id  System
/dev/sde1           31+ 732572032- 732572001   da  Non-FS data
/dev/sde2            0         -          0    0  Empty
/dev/sde3            0         -          0    0  Empty
/dev/sde4            0         -          0    0  Empty
```

---

### Post by djamu on 2009-10-24
mmm strange, 
I recall that I had something similar in the past...

Is this a server that is always running ? did you hotplug those?  > doing a reboot might settle things 
Wipe the partitiontable of the new drives before you do so ... maybe it's a corrupt table > drives tend to fail either very early or late in their livespan .. and because new drives have spare sectors from their own > bad sectors get automatically remapped to spare sectors ( but stay corrupt in the state they where in > not something you really worry about, but in case of a corrupt table better to wipe it & write again

Normally I DD new drives with garbage ( dd if=/dev/random  of=/dev/sdd bs=64k > the complete drive not the individual partitions so bootsectors and partitiontable get overwritten too   ) and then zero them with dd if=/dev/zero of=/dev/sdd bs=64k > in the unlikely case a random sequence resembles a diskstructure ..

Since this will take a while you can try this with only first couple of MB on the disk.... > reboot > repartition > see if it then works ...  

if not > RMA that disk ... or try adding it without partitioning... just for fun ( disks don't need to be partitioned to be added to an array > I tend to partition arrays instead arrays on partitions > then your partitiontable is redundant too )...

---

### Post by fjgaude on 2009-10-24
After going over again the data you presented, I'm confused. You don't use --examine on an array. I don't understand the 'da Non-FS data' you get when using --list and sfdisk. When I do that on one of my drives in an array I get 'fd Linux raid autodetect'.

What filesystem are you using.?

---

### Post by treilanin on 2009-10-24
> **fjgaude said:**
> After going over again the data you presented, I'm confused. You don't use --examine on an array. I don't understand the 'da Non-FS data' you get when using --list and sfdisk. When I do that on one of my drives in an array I get 'fd Linux raid autodetect'.

What filesystem are you using.?

In the initial post in this thread I posted the output of "mdadm --examine /dev/md0".  As far as I know this should be using --examine on the array.  If I am incorrect please let me know and I would be more than happy to provide that output.


For information regarding the partition ids, I would suggest looking at [http://linux-raid.osdl.org/index.php/Partition_Types](http://linux-raid.osdl.org/index.php/Partition_Types).  Of note is this excerpt from this page:

If you are using partitions then there are only 2 sensible choices for your partition type: 
 
[LIST]
[*] 0xDA for non-fs data
[*] 0xFD for raid autodetect arrays
[/LIST]
 (From the mdadm 2.6.8 man-page) When creating partition-based arrays using mdadm and version-1.x superblocks, the partition type should be set to 0xDA (non fs-data). This type selection allows for greater precision since using any other type [RAID auto-detect (0xFD) or a GNU/Linux partition (0x83)], might create problems in the event of array recovery through a live cdrom. 

Either of these two will work on a drive being added to the array.  That being said, I have tried adding the drive with both partition labels with no luck.

---

### Post by treilanin on 2009-10-24
> **djamu said:**
> mmm strange, 
I recall that I had something similar in the past...

Is this a server that is always running ? did you hotplug those?  > doing a reboot might settle things 


This server is generally always running.  When I purchased the two new drives, I shut down the server, installed the drives and started the machine back up.  From there I just followed the guide on the Linux-Raid wiki to add the first new drive to the RAID5 array and then re-shape the array onto it.  After that I followed the instructions to grow the Volume (I am using LVM) and then resize the file system.  AFter that point I tried to add the second new drive and was running into this problem.

Now I rebooted the system and the situation is alot worse now :(.  When LVM attempts to start up it complains with the following message before it dumps me down to the init console:

```
fsck.ext3: No such file or directory while trying to open /dev/mapper/DataVol00-DataVol00
/dev/mapper/DataVol00-DataVol00:
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or nfs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock:
      e2fsck -b 8193 <device>
```

Now if I do a "**mdadm --examine /dev/md0**" I get the following:
```
mdadm: No md superblock detected on /dev/md0
```However running "**cat /proc/mdstat**" gets me the following
```
Personalities: [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0: active raid5 sda[0] sdd1[3] sdc1[2] sdb1[1]
        0 blocks level5. 64k chunk, algorithm 2 [3/3] [UUUU]

unused devices: <none>
```Any ideas?

---

### Post by djamu on 2009-10-25
> **treilanin said:**
> This server is generally always running.  When I purchased the two new drives, I shut down the server, installed the drives and started the machine back up.  From there I just followed the guide on the Linux-Raid wiki to add the first new drive to the RAID5 array and then re-shape the array onto it.  After that I followed the instructions to grow the Volume (I am using LVM) and then resize the file system.  AFter that point I tried to add the second new drive and was running into this problem.

Now I rebooted the system and the situation is alot worse now :(.  When LVM attempts to start up it complains with the following message before it dumps me down to the init console:

```
fsck.ext3: No such file or directory while trying to open /dev/mapper/DataVol00-DataVol00
/dev/mapper/DataVol00-DataVol00:
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or nfs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock:
      e2fsck -b 8193 <device>
```

Now if I do a "**mdadm --examine /dev/md0**" I get the following:
```
mdadm: No md superblock detected on /dev/md0
```However running "**cat /proc/mdstat**" gets me the following
```
Personalities: [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0: active raid5 sda[0] sdd1[3] sdc1[2] sdb1[1]
        0 blocks level5. 64k chunk, algorithm 2 [3/3] [UUUU]

unused devices: <none>
```Any ideas?

be carefull now, **DO NOT run fsck .... your data will be toasted** if you do
because 1 drive is using the whole device and not the partition 
**look at sda** 
```
md0: active raid5 sda[0] sdd1[3] sdc1[2] sdb1[1]
```

this is most likely caused by a leftover old mdadm superblock from the 1st time you installed the array > you most likely did try a 1st build without partitions on the individual drives...

stop that array
and rebuild it ( **with the missing statement  ** )  > 

did you mount it after growing ? , use the amount of disks you had in the last accessible 
state.  if it's 4 disks > use only 3 and replace the 4th with the missing statement > this prevents the raid from a possible wrong resync ( and toasting your data )...
you need to place them in the sequence indicated by the red colored raiddevice nr.
```
    Number   Major   Minor   RaidDevice State
       0       8        1        [COLOR="Red"]**0**[/COLOR]      active sync   /dev/sda1
       1       8       17        [COLOR="red"]**1**[/COLOR]      active sync   /dev/sdb1
       2       8       33        [COLOR="red"]**2**[/COLOR]      active sync   /dev/sdc1
       3       8       49        [COLOR="red"]**3**[/COLOR]      active sync   /dev/sdd1
```

but since the sequence in which you have to put the disks can be shifted > you 
need to examine ( mdadm -E /dev/sda1 ) the individual partitions

then you do > with 3 disks if it worked with 4

```
mdadm --create /dev/md0  --level=5 --raid-devices=4  /dev/sda1 /dev/sdb1/ /dev/sdc1 [COLOR="red"]**missing**[/COLOR] 
```

this will re-create new raidsuperblocks without affecting your data > then try to mount it ( just use mount /dev/md0 /media/storage without any parameters,  let the system try to autodetect it ) 
-if it works add the missing disk and let it re-sync
-if it doesn't  > repeat above step using a different sequence but **always** with the missing statement

finally if it mounted and is resynced > do a fsck
remove the old /etc/mdadm/mdadm.conf > and recreate it ( the new re-created MD device has a new different UUID )
please do read my other posts on this subject.... and if possible  > DD dump the contents of the HD's to a couple of files and use those to practice recreating ( using loopdevices )...

I do this on a regular basis with client arrays ( those who are not that versed, but think they are.... ) so I can assure you ( if you not already tried fsck ) that you will get your data back if you do exactly as I say..... and for all stay calm, don't panic ....

I can perform this service for you if that makes you feel more comfortable, PM me then ...


Jan

---

### Post by treilanin on 2009-10-25
Djamu,

Thank for the reply.  I did the following steps so far:

1. Stopped the array using "mdadm --stop /dev/md0"
2. Re-created the array using "mdadm --create /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 missing". I answered yes to the message to continue even though /dev/sda1 /dev/sdb1 and /dec/sdc1 belonged to an existing RAID device.
3. THe raid started up and can now see the raid device in /dev/disks/by-UUID and through the blkid commands.
4. I mounted the drive (well the LVM volume mount).
5. Could go to the raid and see my files.
6. Added the fourth drive to the array using "mdadm /dev/md0 --add /dev/sdd1"

The array is currently re-syncing.

So I guess the inevitable question will be.... what the heck did I do wrong to cause the superblocks to get corrupted?

Will post a follow up once the re-syncing is completed.  Thanks once again Djamu, I was faced with telling my wife that all of my daughters photos from Birth to now were gone.

Abe

---

### Post by djamu on 2009-10-25
> **treilanin said:**
> Djamu,
snipsnip.....

So I guess the inevitable question will be.... what the heck did I do wrong to cause the superblocks to get corrupted?


propably nothing... adding those new drives, in conjunction with leftover MDADM superblocks caused a shift in drive names and got mdadm confused ... ( this is also why I spoke of completely wiping disks .... to erase leftovers > not all sectors are used for data.. a couple of them hold diskstructure info ) > and most likely also because you did a growth ..... 
also older mdam versions where lacking in using UUID's
be sure to re-create the > /etc/mdadm/mdadm.conf ( auto create )
older mdadm versions didn't really need it > but the latest versions do a good job in fully utilizing UUID's ( also remember that each device has it's own superblocks > the HD's, the MD device itself AND the LVM volumes have their own superblocks and UUID's...  differentiate between them  :)
lastly make sure you fully update the OS when finished resyncing

> 
Will post a follow up once the re-syncing is completed.  Thanks once again Djamu, I was faced with telling my wife that all of my daughters photos from Birth to now were gone.
Abe
 :guitar:
you're welcome ..

---

