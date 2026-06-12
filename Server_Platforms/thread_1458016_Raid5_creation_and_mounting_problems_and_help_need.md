---
title: "Raid5 creation and mounting problems and help needed"
date: 2010-04-19
forum: Server Platforms
---

### Post by speed32219 on 2010-04-19
I installed Raid5 on 3 new 1.5TB disks. I also installed LVM2 but had some problems.  Re-installed karmic server, re-formatted disks and found out that LVM2 is always there lurking in the background somewhere even when it is not installed. (I finally zeroed out the first 512Bytes of the new drives, since that is where I figured LVM2 was lurking, sudo dd if=/dev/zero of=/dev/sd[bcd] bs=512 count=1)  

Well to my dismay, that didn't fix my problem, so I need some guidance. When I first install the Raid5 array I can mount it and copy files and everything is just fine.  But when I shutdown and reboot it doesn't come up and I can't manually mount it.  I am now getting ext4 errors and lvm2 errors.

To keep this short here is my outputs.
uname -a
2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux

```
 sudo fdisk -l
[sudo] password for gellex:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011ea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c7471a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182402  1465138552   fd  Linux raid autodetect

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50610834

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465138552   fd  Linux raid autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24287c0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182402  1465138552   fd  Linux raid autodetect

WARNING: The size of this disk is 3.0 TB (3000603639808 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).


Disk /dev/md1: 3000.6 GB, 3000603639808 bytes
255 heads, 63 sectors/track, 364802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c7471a6

    Device Boot      Start         End      Blocks   Id  System
/dev/md1p1               1      182402  1465138552   fd  Linux raid autodetect

Disk /dev/sde: 2051 MB, 2051014656 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e558f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         158     1269103+  83  Linux
/dev/sde2             159         213      441787+  83  Linux
/dev/sde3             214         249      289170    5  Extended
/dev/sde5             214         249      289138+  82  Linux swap / Solaris
```

sudo ls /dev/md*
/dev/md1  **/dev/md1p1**
What is this highlighted dev above.  It also shows in fdisk -l above.

 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdc[0] sdb[1] sdd[2]
      2930276992 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=14bcca7f-f833-4032-a21f-b9e363adf434 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdd2 during installation
UUID=344ba14e-b4fb-4618-bfd8-e3698fdf7ba6 /home           ext3    defaults        0       2
# swap was on /dev/sdd5 during installation
UUID=946d1e81-ba83-4151-be9a-775af44e66f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# Raid Array
/dev/md1        /media/raid             ext4           defaults          0              2
#NoN Array Drives
/dev/sda1       /media/disk-1           ext3       defaults      0              0

```

sudo mount /dev/md1
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail
[   19.000009] eth0: no IPv6 routers present
[  535.994159] EXT4-fs (md1): VFS: **Can't find ext4 filesystem**
[ 4010.533602] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 5062.353487] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 5071.113853] EXT4-fs (md1): VFS: Can't find ext4 filesystem

 sudo mount /dev/md1 /media/raid
mount: unknown filesystem type 'LVM2_member'

**There is that LVM2 cropping up again!**

Here is the command I used to create the raid5.
mdadm --create /dev/md1 --chunk=1024 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1

Here is the command used to make ext4 filesystem.
mkfs.ext4 -v -m .1 -b 4096 -E stride=32,stripe-width=64 /dev/md1

Here is my mdadm.conf
```
 cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sd[bcd]1


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md1 level=raid5 num-devices=3 metadata=0.90 UUID=45ec6290:e56ae2c4:d66a740f:8642d62d

#Email address in case of failure
MAILADDR gellex1@bellsouth.net

# This file was auto-generated on Sun, 18 Apr 2010 23:55:29 -0400
# by mkconf $Id$

```

 sudo mdadm --examine --scan
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=45ec6290:e56ae2c4:d66a740f:8642d62d

This is interesting
 **sudo mdadm --examine --scan --config=disks**
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=7e6f942e:fb608064:d66a740f:8642d62d
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=45ec6290:e56ae2c4:d66a740f:8642d62d

There must be something out there on one of the disks, but I zeroed them out and reformatted from ext3 to ext4 filesystem.

I need some guidance and hopefully I do not need to re-install.  I've done that 4 times so far. :(

---

### Post by Cracauer on 2010-04-19
Where does LVM come in here?

ETA: the LVM2 info is past the first 512 bytes on the drive. 512 bytes is just the partition table alone. 

This doesn't explain why you can't mount the FS. You say this is after reboot? What does /proc/mdstat say after reboot?

---

### Post by speed32219 on 2010-04-19
I says everything is good.  It always has, I just can't mount the file-system manually or auto after I reboot.  It always gives me a either busy, wrong fs type or bad superblock.

Currently:
 cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdc[0] sdb[1] sdd[2]
      2930276992 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

sudo mount /media/raid
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

sudo mount /dev/md1
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 **dmesg | tail**
[   19.000009] eth0: no IPv6 routers present
[  535.994159] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 4010.533602] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 5062.353487] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 5071.113853] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 5234.973424] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[ 6593.783550] EXT4-fs (md1): VFS: Can't find ext4 filesystem
[20897.074006] EXT4-fs (md1): VFS: Can't find ext4 filesystem


As far as lvm, when I first set it up I also added LVM2.  But like a dumb butt I named the LV media, which is where I mount my other HD's.  So I re-installed and tried LVM again, but it kept changing names and such (vg3 to vg1) that's when I started to zero out the drives, and this time I put ext4 on them instead of 3 figuring it would wipe the drives clean.  Guess I was wrong or something is backed up in my OS.  SO that is where LVM comes in, I really want it but I figure once I get the raid5 working right I can add lvm2.

I put around 80GB on the raid this morning, then I did a shutdown/reboot and it didn't auto mount and I can't manually mount it. But it is started according to mdstat.

---

### Post by speed32219 on 2010-04-19
In trying to get rid of the LVM and clean the drives I used gparted and partitioned the drives.  I figured when I created the raid5 and I fdisk -u on each individual to delete the partions and create anew one with raid that it would take care of LVM and anything else.

I just ran fdisk on the array, since running it on each drive showed no errors. Maybe this is normal for a RAID5 since this is my first one, but the mention of the DOS partition table bothers me.

sudo fdisk -l /dev/md1

WARNING: The size of this disk is 3.0 TB (3000603639808 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID
partition table format (GPT).

I am going to try and do some force mounts to see if that does anything.

---

### Post by speed32219 on 2010-04-20
Well, I will try this again with a 1 TB drive I will have after I move everything over to the new Radi5/LVM.

Yes, I finally got it to work by installing LVM2.
sudo pvcreate -FF /dev/md1 (I had to use the -FF command)
sudo vgcreate vg1 /dev/md1
sudo lvcreate -L 2.7T -n raid vg1

And the most important, which this may be the step I missed with the Raid.

sudo mke2fs -j /dev/vg1/raid   (place a file system on the RAID device) 

Took much goggling and a fresh install of karmic server with upgrade. I am now copying files over at > 90MB/sec.

---

### Post by Cracauer on 2010-04-20
But your first post said you created a filesystem (ext4fs)?

---

### Post by speed32219 on 2010-04-20
you have keen eyesight, must be a techie. :)

I did and it bothers me, wish you wouldn't have brought that up.  Just as I hit enter for the mke2fs -j I realized it was for an ext3 file-system. I left it build the inodes and to my disbelief it works.  What the impact is or will be is beyond me, but there are no errors. Except I still can not mount raid5 md0 array, but instead have to mount the lvm vg1, which also bothers me.

sudo mount /dev/vg1/raid /mnt/raid

---

