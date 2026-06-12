---
title: "Bad superblock /dev/md0 softraid 10.04 server"
date: 2011-03-24
forum: Server Platforms
---

### Post by bgood on 2011-03-24
This might take a little while to explain so please bear with me.

I just bought a HP N36L microserver to replace my Netgear ReadyNAS as it has 4 bays as opposed to the 2 in the Netgear, the HP came with a 250GB Seagate drive in so I installed Ubuntu 10.04 server onto  that as a minimal install in a 5GB partition, selected basic server,  lamp and samba during the setup and then once installed added the  minimal gui, all good so far.

The idea was to have 3 1TB drives in the HP running software Raid 5 and after trying to do this via the disk utility gui and having misaligned cylinders I found this guide for setting up the Raid 5 array - [http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/](http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/)

Now the problem with setting up the raid was I had just over 900GB of data on the 2 disks in the Netgear and not enough space anywhere to back it all up so the plan was to install 1 x 1TB drive and format to ext4 and transfer all the data onto it from the Netgear, then pull the 2 drives from the Netgear and build the Raid 5 array using just those 2, then copy the data from the 3rd drive onto the raid and then add the 3rd drive and grow the array.

This actually was all going fine, 2 disk array was built, data transferred and all was good so added the 3rd drive to the array and issued the grow command, after many hours this completed and I had a 2.0TB filesystem icon on the desktop.

Now the problem, the last two steps were to unmount the array and run an fsck on it (as per the guide) and then grow the filesystem but the array wouldn't unmount it kept saying it was busy, I tried to force it but still nothing so I decided to reboot (my windows background coming back to haunt me perhaps) when the box came back up it failed to mount the array due to a bad superblock :(

If I try and run the fsck on the array now I get this

```
bg@NAS:~$ sudo fsck /dev/md0
[sudo] password for bg:
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```So in an effort to try and fix it I did something which I think may have really screwed things up, in the disk utility it lists 2 arrays and there was an option on 1 of them for "check and repair" which I clicked and it said it was resyncing but I then realised there was only 2 components as this was the first array I'd built with the misaligned cylinders so I quickly stopped it but I really don't think this has helped things, oops!

So is it possible to rebuild the array back to the point where it was i.e. a 3 disk array? or at the very least can I recover my data somehow?

Some info that may be useful:

```
bg@NAS:~$ sudo mdadm --assemble --scan --verbose
mdadm: metadata format 00.90 unknown, ignored.
mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/block/9:0
mdadm: no RAID superblock on /dev/sdd
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/md/0 already active, cannot restart it!
mdadm:   /dev/md/0 needed for /dev/sdd1...
mdadm: looking for devices for /dev/md/0
mdadm: no RAID superblock on /dev/sdd

``````
bg@NAS:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8edb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4881408   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             609       30401   239312272+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c59f

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c59f

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000921b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux RAID autodetect

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
2 heads, 4 sectors/track, 244190624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 65536 bytes
Disk identifier: 0x0008c59f

    Device Boot      Start         End      Blocks   Id  System
```Before I stupidly clicked on the check and repair option in the disk utility there were 3 devices showing in the below
```
bg@NAS:~$ sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Sat Mar 19 21:07:47 2011
     Raid Level : raid5
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 24 10:01:22 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d541cc86:71de22fe:cced5de7:ca715931 (local to host NAS)
         Events : 0.92

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
```

---

### Post by rubylaser on 2011-03-24
What's the output of this command on each mdadm disk?
```
mdadm -E /dev/sdb
```
```
mdadm -E /dev/sdc
```
```
mdadm -E /dev/sdd1
```
(I'm guessing these are the proper disks / partitions based on what I'm seeing in your fdisk -l).

And what do you have in /etc/fstab?
```
cat /etc/fstab
```

Finally, what does your mdadm.conf file look like?
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by bgood on 2011-03-24
Thanks very much for taking the time to reply rubylaser, here's the output you requested:

```
bg@NAS:~$ sudo mdadm -E /dev/sdb
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d541cc86:71de22fe:cced5de7:ca715931 (local to host NAS)
  Creation Time : Sat Mar 19 21:07:47 2011
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu Mar 24 10:47:15 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5cf36a00 - correct
         Events : 92

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
bg@NAS:~$ sudo mdadm -E /dev/sdc
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d541cc86:71de22fe:cced5de7:ca715931 (local to host NAS)
  Creation Time : Sat Mar 19 21:07:47 2011
     Raid Level : raid5
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu Mar 24 10:47:15 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5cf36a12 - correct
         Events : 92

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       32        1      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
bg@NAS:~$ sudo mdadm -E /dev/sdd1
mdadm: metadata format 00.90 unknown, ignored.
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 655b4b3c:31a216e8:cced5de7:ca715931 (local to host NAS)
  Creation Time : Tue Mar 22 08:10:17 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Wed Mar 23 15:19:24 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : acd36c8c - correct
         Events : 14036

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       49        2      active sync   /dev/sdd1

   0     0       8       17        0      active sync
   1     1       8       33        1      active sync
   2     2       8       49        2      active sync   /dev/sdd1
```I've commented out the line for mounting the raid for the moment as I'm still using the box for other things and if for some reason I need to reboot it remotely it will just hang when it fails to mount the raid.

```
bg@NAS:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=29a8e149-4965-48ff-86b1-00eaecdb5027 /               ext4    errors=remount-ro 0       1

/dev/sda2       /media/Backup   ext4    rw              0       0

#/dev/md0       /media/Raid     ext4    rw              0       0

#192.168.1.1:/media/Music /media/music nfs rsize=8192,wsize=8192,timeo=14,intr
#192.168.1.1:/media/Videos /media/video nfs rsize=8192,wsize=8192,timeo=14,intr
``````
bg@NAS:~$ cat /etc/mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid5 num-devices=2 metadata=00.90 UUID=655b4b3c:31a216e8:cced5de7:ca715931

# This file was auto-generated on Sat, 19 Mar 2011 19:36:04 +0000
# by mkconf $Id$
```

---

### Post by rubylaser on 2011-03-24
Wow, you have a mess on your hands there.  sdb, and sdc are showing the same info, so I would remove sdd from the system, or zero it's superblock, and then reboot.  Your mdadm.conf file looks okay (except that it's showing 2 devices instead of 3), but they superblocks on your disks are what's screwing it up.

I would tell, you to try to update your mdadm.conf to reflect the 3 devices instead of 2, but sdb and sdc's superblocks still show 2 devices so this won't help.

After removing sdd, and rebooting, if your array does come up, without mounting it,  you should try to fsck it like this...

```
sudo -i
fsck.ext4 /dev/md0
```

If that works, you then should find a way to backup your data first. Once, you've backed it up, then you can proceed to add the disk back in like this...

```
sudo mdadm --grow --bitmap=internal /dev/md0
sudo mdadm --add /dev/md0 /dev/sdd1
sudo mdadm --grow /dev/md0 --raid-devices=3
```

You can follow the progress by checking the file /proc/mdstat.

```
watch cat /proc/mdstat
```
I like wait for the operation to finish before attempting to grow the filesystem, but you should be able to do it while the array syncs.

Once array rebuild or fully synced, disable bitmaps:

```
sudo mdadm --grow --bitmap=none /dev/md0
```

**Growing the filesystem**

Before you can grow the filesystem you need to unmount it. Now that it is unmounted you can run a filesystem check to make sure everything is in order:

```
sudo fsck.ext4 -f /dev/md0
```
If any issues arise, let it attempt to fix them for you.

Once the filesystem has been checked you can perform the resize.
```
sudo resize2fs /dev/md0
```
This will automatically grow the filesystem to the new size of the device.

Finally, update your mdadm.conf file to reflect the changes.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by bgood on 2011-03-24
I removed sdd and booted back up and the array is running so tried to fsck it but no dice :(

```
root@NAS:~# fsck.ext4 /dev/md0
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```Really appreciate your help on this, what should I try next?

---

### Post by rubylaser on 2011-03-24
You'll need to see if you can find an alternate superblock like it's suggesting you do.
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")

---

### Post by bgood on 2011-03-24
Oh dear, looks like I've properly broken it, tried all the backup superblocks and none of them worked :(


Fortunately I did backup at least some of the data and none of the files I've lost are unique so I can recreate them all but it will be a fairly lengthy process, ho hum.



mutter, mutter, mutter, always backup, always backup, always backup!

---

### Post by rubylaser on 2011-03-24
If, that's the case, you can be a bit more aggressive.  Have you tried to assemble what you have?  Stop /dev/md0, and then try this...
```
sudo -i
mdadm -S /dev/md0
mdadm --assemble /dev/md0 --uuid=655b4b3c:31a216e8:cced5de7:ca715931
```

---

### Post by bgood on 2011-03-24
It doesn't want to do that apparently

```
root@NAS:~# mdadm --assemble /dev/md0 --uuid=655b4b3c:31a216e8:cced5de7:ca715931
mdadm: metadata format 00.90 unknown, ignored.
mdadm: no devices found for /dev/md0
```

---

### Post by rubylaser on 2011-03-24
Okay, here's a more aggressive version :)

```
mdadm --assemble --force /dev/md0 /dev/sdb /dev/sdc /dev/sdd1
```

---

### Post by bgood on 2011-03-24
I take it I should run that command without /dev/sdd1 as that disk is currently removed or do you want me to put it back in?

---

### Post by rubylaser on 2011-03-24
Sorry, I should have explained that.  You'll want to put the disk back in.  It's UUID matches the other one's, but it's disk layout was different, so I wanted to have you try it with it out first.

---

### Post by bgood on 2011-03-24
Ok no probs, might be a couple of hours now before I can try that.

---

### Post by rubylaser on 2011-03-24
If forcing it back together doesn't work, then you can try to run create command again (won't overwrite your data).

```
mdadm --create /dev/md0 -v -l 5 -n 3 /dev/sdb /dev/sdc /dev/sdd1
```

That may or may not actually assemble the array.  If it doesn't, just assemble it.
```
mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd1
```

If that does work, make sure to update your mdadm.conf file like I showed earlier.

---

### Post by bgood on 2011-03-24
Okay so "mdadm --assemble --force /dev/md0 /dev/sdb /dev/sdc /dev/sdd1" didn't work, sorry can't remember what it said now because after that I ran "mdadm --create /dev/md0 -v -l 5 -n 3 /dev/sdb /dev/sdc /dev/sdd1" which worked and then did a "sudo watch cat /proc/mdstat" that wiped out my putty window history.

Anyway the good news is as you can see below it's recovering and it's listed in the Disk Utility as a 2.0TB array, so things are looking up :)

```
Every 2.0s: cat /proc/mdstat                                                Thu Mar 24 21:15:15 2011

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3] sdc[1] sdb[0]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.6% (5960860/976759936) finish=301.5min speed=53649K/sec

unused devices: <none>
```As it's gonna take about 5 hours will check it in the morning, time for bed here and looks like it must be nearly time for you to clock off work over in Michigan rubylaser, thanks again for the help, will update you tomorrow with progress.

---

### Post by rubylaser on 2011-03-24
It's only about 6 P.M. here, so I hope it's not time for bed :)  Glad to see that's working for you.  You'll want to remember to update your mdadm.conf file like this...
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

And, did you verify that your data was intact?

---

### Post by bgood on 2011-03-24
I was gonna let it finish recovering before I did anything, didn't want to break anything else :-)  

Is it safe to start and mount the array now, also what's the correct command to check if the array is actually running and if it's not what do you use to start it?

Oh and don't worry I noted what you said about updating mdadm.conf so will def do that.

---

### Post by rubylaser on 2011-03-24
If it shows up via cat /proc/mdstat (it does because it's rebuilding), it's okay to try mount it I just wouldn't do any writing to it until it's in sync.  If it fails to mount because you need to run a filesystem check (fsck), I'd wait until it finished syncing before I did that.

---

### Post by bgood on 2011-03-25
Hmmmm, the sync has finished so tried to run an fsck but still getting a superblock problem.

```
bg@NAS:~$ sudo -i
root@NAS:~# fsck.ext4 /dev/md0
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

In the disk utility gui it shows a 2.0TB array as idle and with 2.0TB of free space and the only option is to create a partition, that doesn't look good as far as recovering the data is concerned :-(

The array itself at least looks a bit more like it should.

```
bg@NAS:~$ sudo mdadm --misc --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Thu Mar 24 21:13:17 2011
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Mar 25 02:33:34 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 9c318032:cda39a33:cced5de7:ca715931 (local to host NAS)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       49        2      active sync   /dev/sdd1

```

---

### Post by rubylaser on 2011-03-25
Have you tried to look at the superblocks again.  This is looking like the filesystem got hosed from the split brain RAID. 

```
mke2fs -t ext4 -n /dev/md0
```

Then try all of the superblock locations it gives you.

```
e2fsck -b 98304 /dev/md0
```

If you still have no valid superblocks, I'm not sure where to go from there.  You have a valid RAID set now, but it looks like the filesystem didn't survive the initial check/repair on the RAID set :(

---

### Post by bgood on 2011-03-25
Looks like it's beyond repair, tried all the backup superblocks and none of them worked, you'd never guess I've never touched mdadm or softraid in Ubuntu until I tried setting this up would you ;-)

Oh well, lessons learned I suppose, so was it the reboot that broke it or clicking on that 'check and repair' option in the gui, I'm guessing it was the gui more so?

If it is beyond redemption what's the best way of tearing it all down and rebuilding it properly from scratch with the 3 discs?

---

### Post by rubylaser on 2011-03-25
That stinks... I would wager that it was the GUI check/repair action that broke it.  The good news, is you don't need to tear anything down.  mdadm has the disks in sync, you just need to add a filesystem to the array now.

```
sudo mkfs.ext4 /dev/md0
```
```
sudo tune2fs -m 0 /dev/md0
```

And add a line to your /etc/fstab to mount the array for you.

---

### Post by bgood on 2011-03-25
Yeah thought as much, really should know better than to go clicking on buttons when I don't know what they do, I thought it would bring up some info and then give me some options of what to do not just go off and try and fix stuff :frown:

Only thing I can see about the way it is now that is puzzling me slightly is that the the disk sdd is listed as sdd1 where as sdb & sdc are just listed as sdb & sdc as below, is there a reason they are different and does it matter (sorry but I like things to be nice and neat and match up, perhaps I'm just being fussy here)

```
bg@NAS:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb[0] sdd1[2] sdc[1]
      1953519872 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

```

---

### Post by rubylaser on 2011-03-25
The reason that they're that way is sdb and sdc are using the whole raw disk, sdd is using a partition on the disk (in this case the 1st one).  I like to use partitions on all my RAID devices, but there's no right or wrong way to do it.

Unless, you really feel the need to redo your array, I'd just leave it like it is and throw a filesystem on it.  Otherwise, stop and remove md0, zero the superblocks on each drive / partition, remove your mdadm.conf file, then use fdisk on sdb and sdc to add partitions to them so that they can be the same and sdd.  Then, you'd need to rebuild the array, and add a new mdadm.conf file, and finally the filesystem.

---

### Post by bgood on 2011-03-25
I might redo it cos sadly that's the sort of thing that will bug me, will decide tomorrow.

Anyway more importantly I'd like to say a huge thanks to you rubylaser for all your help, you're a legend :-)

---

### Post by rubylaser on 2011-03-25
No problem, just wish we could have recovered your filesystem.  As a side note, I would redo all of the disks to partitions too, because that kind of thing would drive me crazy, and could potentially lead to an error if you need to perform any maintenance on the array in the future.

---

### Post by bgood on 2011-03-26
Seems you and I are on the same wavelength rubylaser ;-)

I've torn down the array, zeroed the superblocks and built it again from scratch, looking much better now :)

```
bg@NAS:~$ sudo mdadm --detail /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
/dev/md0:
        Version : 00.90
  Creation Time : Fri Mar 25 22:30:00 2011
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Mar 26 07:51:15 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93862cea:666ca201:b8756c74:3dd5f86e (local to host fileserver)
         Events : 0.35

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1

```

```
bg@NAS:~$ cat /etc/mdadm/mdadm.conf
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 level=raid5 num-devices=3 metadata=00.90 UUID=93862cea:666ca201:b8756c74:3dd5f86e

```

```
bg@NAS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4.6G  2.8G  1.8G  62% /
none                  936M  228K  936M   1% /dev
none                  941M   92K  941M   1% /dev/shm
none                  941M  3.6M  937M   1% /var/run
none                  941M     0  941M   0% /var/lock
none                  941M     0  941M   0% /lib/init/rw
/dev/sda2             225G  176G   50G  79% /media/Backup
/dev/md0              1.8T   79G  1.8T   5% /media/Raid

```

---

### Post by rubylaser on 2011-03-26
That looks great.  If you want to get rid of this line 
```
mdadm: metadata format 00.90 unknown, ignored.
```
when you view the mdadm detail for your array, all you need to do is edit your mdadm.conf file to remove one of the leading zeros in metadata section so it changes from this...
```
metadata=00.90
```
to this...
```
metadata=0.90
```
And, then the unkown format errors will disappear.

---

### Post by bgood on 2011-03-26
Thanks for the tip, that's sorted it and everything seems perfect now, just need to fill it with data :D

```
bg@NAS:/media$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Mar 25 22:30:00 2011
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Mar 26 13:59:27 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93862cea:666ca201:b8756c74:3dd5f86e (local to host fileserver)
         Events : 0.34

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1

```

---

