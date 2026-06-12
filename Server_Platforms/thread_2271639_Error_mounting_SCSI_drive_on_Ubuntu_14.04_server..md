---
title: "Error mounting SCSI drive on Ubuntu 14.04 server."
date: 2015-03-31
forum: Server Platforms
---

### Post by Geza_Fischer on 2015-03-31
I'm trying to mount a SCSI Drive on my Ubuntu 14.04 server.
To mount I entered this in the Terminal:
 geza@Server1:~$ sudo mount -t ext4 /dev/sdb /media/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Then I did a fsck:
    geza@Server1:~$ sudo fsck.ext4 /dev/sdb
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

geza@Server1:~$
I posted this on Askubuntu.com and they told me to do a fdisk -l /dev/sdb .

It couldn't find the /dev/sdb disk it could only find the /dev/sda disk which is the other 2 drives on the server configured with RAID 1.

What should I do?

Thanks 
  Geza

---

### Post by darkod on 2015-03-31
First, you can't mount the disk directly as you are trying to. Your command tries to mount /dev/sdb which is the whole hdd. You mount partitions, and you have to create the ext4 filesystem before that. It doesn't simply mount when not created.

So, you need to use parted or fdisk or which ever partitioning tool you are familiar with to make partitions on /dev/sdb, then format those partitions, and then try to mount the partitions (or a single partition on the whole disk, if you want that).

If ubuntu sees only sda and not the sdb disk, then maybe it doesn't have the drivers to read the scsi adapter (and the disk attached to it), etc... So you need to look into that matter first because you can't use the disk until you can see it.

---

### Post by Geza_Fischer on 2015-03-31
The drive has an ext4 file system set up on it already. And it has to have the drivers because it was working a few weeks ago.

Thanks
Geza

---

### Post by darkod on 2015-04-01
Ok. But you are still trying to mount it wrong. /dev/sdb is the whole disk. To mount a specific partition you use the partition number at the end, like /dev/sdb1. Also for ext4 you don't need to use the -t option. You can simply use:
```
sudo mount /dev/sdb1 /media/sdb
```

Also /media is usually used by the system for auto temporary mounts. You can create any mount point you want and use that instead of /media.

To see all disks and partitions show us the output of:
```
sudo parted -l (that is small L)
```

That will help figure out which partitions you have and their filesystem.

---

### Post by Geza_Fischer on 2015-04-01
See the problem is that Ubuntu doesn't recognize the disk. Here is the output of sudo parted -l :

```

geza@Server1:~$ sudo parted -l
[sudo] password for geza:
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Model: MegaRAID LD 0 RAID1 286G (scsi)
Disk /dev/sda: 300GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  30.0GB  30.0GB  primary   ext4            boot
 2      30.0GB  300GB   270GB   extended
 5      30.0GB  298GB   268GB   logical   ext4
 6      298GB   300GB   2145MB  logical   linux-swap(v1)

Error: /dev/sdb: unrecognised disk label
geza@Server1:~$
 

```



Thanks

 Geza

---

### Post by darkod on 2015-04-01
Well it seems it knows sdb is there but can't read it. Maybe the disk got faulty/died or something?

---

### Post by Geza_Fischer on 2015-04-01
I'm not sure. It's pretty old. Is there a way to recover it?

Thanks
  Geza

---

### Post by darkod on 2015-04-02
Unfortunately if it doesn't read the disk correctly it would be very difficult to reach the data. Do you have a backup? If you do you can simply buy a new disk and put the data back.

---

### Post by Geza_Fischer on 2015-04-03
No I don't have a backup. That drive was the backup and that's why I was trying to move it to the 2 new drives I just got. The other old drive corrupted 1 month ago. Is it possible to repair it from the backup Superblocks? I tried a few tutorials on the internet for doing an # fdisk -b (superblock) /dev/sdb  but every time I did it, it didn't put out a response. I tried all the backup SB's. Anything else I can do?

Thanks
Geza

---

