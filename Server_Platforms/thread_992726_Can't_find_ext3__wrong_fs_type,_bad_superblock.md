---
title: "Can't find ext3 / wrong fs type, bad superblock"
date: 2008-11-25
forum: Server Platforms
---

### Post by matt_lethargic on 2008-11-25
Firstly, sorry if this post is in wrong place, bit of a noob here and first post on Ubuntu forums.

I've just bought a secondhand 160GB SATA HD, put in pc, booted, run fdisk to delete FAT16(!) partition and create a new one. Now I can't mount it, I've tried loads of different things that I've searched for, but no one seems to have my exact problem. 

/dev/sdc
8.10 server
P4
1GB Ram

fdisk -l

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e2b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae03ae03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       20023   160834716   83  Linux

```

mount -l

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /media/endor type ext3 (rw,errors=remount-ro) []
securityfs on /sys/kernel/security type securityfs (rw)
```

mount -t ext3 /dev/sdc1 /media/hoth

```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg | tail

```
[120543.554819] VFS: Can't find ext3 filesystem on dev sdc1.
```

fdisk /dev/sdc1 -l
```
Disk /dev/sdc1: 164.6 GB, 164694749184 bytes
255 heads, 63 sectors/track, 20022 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System

```

.....? confused now!

fsck /dev/sdc1 & fsck /dev/sdc
```
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

e2fsck -b 8193 /dev/sdc
```
e2fsck 1.41.3 (12-Oct-2008)
e2fsck: Bad magic number in super-block while trying to open /dev/sdc1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```


Not sure where to go with this now, any more info needed let me know, as I said I'm a noob and am at the end of my knowledge. I really need this space now as I'm trying to use this as my media server and I've got films to rip!

---

### Post by matt_lethargic on 2008-11-25
I have just found
[https://answers.launchpad.net/ubuntu/+question/10671]("https://answers.launchpad.net/ubuntu/+question/10671")

and tried
sudo file -s /dev/sdc1
```

/dev/sdc1: x86 boot sector

```

I then tried:

sudo mke2fs -S /dev/sdc1
```
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
10059776 inodes, 40208679 blocks
2010433 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1228 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```

sudo mke2fs -j /dev/sdc1
```
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
10059776 inodes, 40208679 blocks
2010433 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1228 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
```


now
sudo file -s /dev/sdc1
```

/dev/sdc1: Linux rev 1.0 ext3 filesystem data (large files)

```

That seems better.... mounts first time.
So if I was a betting man I would say that I need to learn how to create partitions! When I create a partition in fdisk do I then have to use mke2fs to format it or something?

---

### Post by vanadium on 2008-11-25
The partition is there, but it looks as if it is not (properly) formatted. Try formatting it (again), using gparted or with the following command. In fact, you'd better use the command and if error messages appear, copy paste them here, it would help to identify the problem (if any)

```

sudo mkfs -t ext3 /dev/sdc1

```

---

### Post by matt_lethargic on 2008-11-25
Is there a difference between mke2fs and mkfs? As I said I used mke2fs and it works fine now.

---

### Post by MJN on 2008-11-25
Read the man page(s)!
 
mkfs is just a generic front end to other filesystem creation tools hence if you execute **mkfs -t ext3** it calls mke2fs (given the ext3 type specifier) with the necessary options to build an ext3 filesystem (which is equivalent to a journaled ext2 system hence your -j flag).
 
To put it another (simpler!) way; they are merely two different routes to the same result.
 
Mathew

---

### Post by vanadium on 2008-11-25
You did find the proper solution before seing my post ;)

```
When I create a partition in fdisk do I then have to use mke2fs to format it or something? 
```

Partitions and file systems are a different thing indeed. You first partition a drive, and then you format the partition(s) with the file system of your choice.

---

