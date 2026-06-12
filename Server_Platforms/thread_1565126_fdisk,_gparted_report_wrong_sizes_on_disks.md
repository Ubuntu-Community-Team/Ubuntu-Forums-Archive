---
title: "fdisk, gparted report wrong sizes on disks"
date: 2010-08-31
forum: Server Platforms
---

### Post by soltanis on 2010-08-31
I have some WD20EARS drives that I am trying to format into a pair of Linux software RAID1 devices. The problem is that at seemingly random steps during the process, the operating system decides the disk is a size much smaller than it actually is (2 TB, or as reported by the OS when it is acting normal, 1.82 TB).

I follow this general layout of steps: first, I do fdisk -u /dev/sd[x], create a primary partition spanning the whole disk starting from sector 64 (to align the advanced format blocks properly). I set the partition type to fd (software RAID autodetect). Then, I assemble the arrays with mdadm:

```

mdadm --create /dev/md[z] --level=raid1 --raid-devices=2 /dev/sd[x]1 dev/sd[y]1

```

And then I create an ext4 filesystem:

```

mkfs.ext4 /dev/md[z]

```

For reasons I can't understand, fdisk, parted, and gparted (basically, everything) decides at any random point in that process that my disks are not 1.82 TB, but instead something like 172 GB or 500 GB. Once that happens, nothing I do to try to get my disks back seems to work. I've tried using expert mode in fdisk to manually reset the number of cylinders to the correct amount, but this hasn't worked either. Nothing short of reinstalling the system seems to work (but when I boot the installer, it seems to recognize the correct size of the disks).

Has anyone else ever had this problem? What the heck is going on?

---

### Post by craigp84 on 2010-08-31
In between the fdisk and the mdadm i'd have done a partprobe to instruct the kernel about my changes, otherwise it will get confused until you reboot.

---

### Post by soltanis on 2010-08-31
Interesting, first time I've heard of this. In any case, reboots didn't seem to solve the problem; even after rebooting the system, the disks would appear to be much smaller than they actually were.

I've managed to figure out that fdisk seems to be ignoring me when I tell it to fill the entire disk with a single primary partition. Perhaps this is because I had DOS mode enabled; I turned it off. However, fdisk still doesn't want to make partitions larger than 1024 GB, so I've switched to using gparted, but that doesn't have any way for me to set the partition to Linux software RAID.

I'm going to try this one more time using parted.

---

### Post by ian dobson on 2010-08-31
Hi,

Try using fdisk with the -u option to specify start/end secotor. The EARS drives are 4K sectors aren't they. If so start the partition at a 4K boundy (Sector number 64 and not the dos standard 63).

I have 2 ears drives in a stripped (RAID1) array for data backup and apart from having to manually align the partition table thy've been running for about 6months now without any problems.

 ```
fdisk -u -l
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1786ce25

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e1d2620

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              64  3907029167  1953514552   fd  Linux raid autodetect

Disk /dev/md2: 4000.8 GB, 4000797556736 bytes
2 heads, 4 sectors/track, 976757216 cylinders, total 7814057728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000
```

Regards
Ian Dobson

---

### Post by soltanis on 2010-09-01
Hi. I actually followed that advice to no avail. I'm currently trying this:

```

# /dev/sdb is the example disk
root # parted
(parted) mklabel gpt
(parted) mkpart primary ext2 1M 2000G
(parted) set 1 raid on

```

On all four disks. It seems that parted 2.2 is smart about advanced format drives and if you try to do

```

(parted) mkpart primary ext2 0 2000G

```

It will inform you that the drives will not be in optimal alignment. According to the [documentation]("http://www.gnu.org/software/parted/manual/html_mono/parted.html") setting the start to 1M informs parted to use optimal partition alignment (or, you can set the units to sectors and also manually align them yourself).

I've now assembled the arrays with
```

mdadm --create /dev/md0 --level=raid1 --raid-devices=2 /dev/sdb1 /dev/sdc1

```

and I'm waiting for a sync before I try rebooting and seeing if the array reassembles itself properly.

---

### Post by ian dobson on 2010-09-01
Hi,

You don't need to partition your raid5 array before formatting it. My main array is a RAID5 array with 4x2Tb drives, and I just formatted /dev/md1 as ext4 without partitioning it. And appears to work. A formatted block device works under linux but other OS's won't see the data (Windows,FreeBSD etc).

Regards
Ian Dobson

---

### Post by soltanis on 2010-09-02
I'm marking this thread as solved. To clear up for anyone else who might stumble across this frustration, this is what I did:

Used parted as described above to partition the disks with a GPT and a Linux Software Raid partition spanning the entire 2 TB disk.

Then, I assembled a raid10 array with:

```

mdadm --create /dev/md0 --level=raid10 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

```

Waited for the array to sync and created an ext4 filesystem on it.

Then, I rebooted the server. At this point, the server failed to correctly start the array up again. It would start two or three inactive arrays with only one or two of the drives in them. To solve this, I manually did:

```

mdadm --stop --scan # to stop all the incorrectly detected arrays
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

```

Since the server wouldn't remember this on restart, even after editing the mdadm.conf file, I finally gave up and edited the script /etc/init.d/mdadm and added two scripts called "start-array" and "stop-array" in the start/stop sections before the initscript ran mdadm --monitor that looked like this:

```

#!/bin/sh
#start-array
mdadm --stop --scan
mdadm --assemble ... # as above
mount /dev/md0 /media/md0

#stop-array
umount /dev/md0
mdadm --stop --scan

```

I included mounting in the mdadm hooks because /etc/fstab tries to mount filesystems before the arrays are assembled which causes the system to wait for user input on reboot. It's a hackish solution, but it works, and is persistent even after reboots/power fails.

---

