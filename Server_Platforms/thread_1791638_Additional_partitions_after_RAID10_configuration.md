---
title: "Additional partitions after RAID10 configuration"
date: 2011-06-27
forum: Server Platforms
---

### Post by gipson on 2011-06-27
Hello, im trying to set software RAID10 (Ubuntu Server 11.04). The drives are 4x 40GB.

_During the installation_:

- Created 2GB partition on every disk for md0 (boot).
- Created 38GB (rest) partition on every disk for md1 (data) - for now it's just one big partition for testing.
- Created RAID1 from 2GB partitions (sda1, sdb1, ...), bootable.
- Created RAID10 from 38GB partitions (sda2, sdb2, ...), EXT4.

_After the installation_:

- Created 1GB swap file on md0 (with mkswap and swapon, added to fstab).
- Reboot.

_What i was expecting to see is_:

**/dev/md0** mounted on **/boot**, about 2GB total, 1 - 1,5GB used for boot files and swap i made.
**/dev/md1** mounted on **/**, about 76GB total (38GB x2, because of RAID10), 1 - 1,5GB used for system files.

_What i do see now is:_:

**df -h** result:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md1               70G  1.1G   66G   2% /
none                  7.9G  272K  7.9G   1% /dev
none                  7.9G     0  7.9G   0% /dev/shm
none                  7.9G   56K  7.9G   1% /var/run
none                  7.9G     0  7.9G   0% /var/lock
/dev/md0              1.9G  1.1G  699M  61% /boot

```

_My questions are_:

**(1)** What are these '**none**' filesystem partitions and why where they created? Why 7.9GB - i didn't set anything like that. Got software RAID1 (2 disks) on different machine and it shows only /dev/mdX, not some additional partitions.

**(2)** Why /dev/md1 isn't 76GB total? During the installation all disks were seen as full 40GB, not smaller. Even if it was, it would be about 40GB / 1024 * 1K ~= 39GB, so minus that 2GB for md0 = 37GB ... x2 ~= 74GB, not 70GB. That's not really a problem, im just curious - maybe im mistaken, because my logics are wrong - im more concerned about these partitions.

**(3)** How large should be swap partition with this configuration? Everywhere i read, people say '2x your RAM' - it would take half of total disk space here!

_Additional informations_:

**fdisk -l**
```

Disk /dev/sda: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e86fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1951744   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         244        4866    37127168   fd  Linux raid autodetect

Disk /dev/sdb: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006d08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951744   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *         244        4866    37127168   fd  Linux raid autodetect

Disk /dev/sdd: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002a1bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         244     1951744   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdd2   *         244        4866    37127168   fd  Linux raid autodetect

Disk /dev/sdc: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00018031

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         244     1951744   fd  Linux raid autodetect
Partition 1 does not end on cylinder boundary.
/dev/sdc2   *         244        4866    37127168   fd  Linux raid autodetect

Disk /dev/md0: 1997 MB, 1997524992 bytes
2 heads, 4 sectors/track, 487677 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 76.0 GB, 76033294336 bytes
2 heads, 4 sectors/track, 18562816 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

```

**cat /etc/fstab**
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=2c789bfe-5da3-4140-be67-bbf067c879ce /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=890d72b1-6b0c-44e9-8e29-d5d1dc03c217 /boot           ext4    defaults        0       2
/boot/1Gb.swap none swap sw 0 0

```

**cat /proc/mdstat**
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid10] [raid6] [raid5] [raid4]
md1 : active raid10 sdc2[2] sdd2[3] sda2[0] sdb2[1]
      74251264 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]

md0 : active raid1 sdc1[2] sdd1[3] sda1[0] sdb1[1]
      1950708 blocks super 1.2 [4/4] [UUUU]

unused devices: <none>

```

**Machine**

Intel i5 3.2GHz, 16GB RAM DDR3, these 4 drives are SSD, 40GB each.

**Destination**

Web server (LAMP) with huge database usage (small number of connections, lots of queries).


I'd really appreciate any information / help.
Also wanted to say im pretty much 'sunday user' of linux, so if my conception is totally wrong, don't be too hard on me.

If i should provide any more system information please let me know, i'll do that asap.

Thank you!

---

### Post by gipson on 2011-06-28
Found info about these 'none' partitions: [http://ubuntuforums.org/showthread.php?t=1670124](http://ubuntuforums.org/showthread.php?t=1670124)

Question about how big should be swap file with this configuration still stands, thanks.

---

