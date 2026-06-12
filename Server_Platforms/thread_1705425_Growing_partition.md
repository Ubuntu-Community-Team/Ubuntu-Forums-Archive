---
title: "Growing partition"
date: 2011-03-12
forum: Server Platforms
---

### Post by 8Kuula on 2011-03-12
My server box system disk stared to get read errors so I got new disk and ran dd_rescue. That part went nicely. System boots and services are runing.

Old disk was 500GB and new one is 1TB, so I would like to grow /home partition to use that extra 500GB

Filesystem is ext4

```
fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000965d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19530752   83  Linux
/dev/sda2            2432       60802   468853761    5  Extended
/dev/sda5            2432        2681     1998848   82  Linux swap / Solaris
/dev/sda6            2681       60802   466853888   83  Linux
```
```
mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /home type ext4 (rw)
/dev/md0 on /mnt/server/raid5 type xfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
```

```
parted /dev/sda print free
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
        32,3kB  1049kB  1016kB            Free Space
 1      1049kB  20,0GB  20,0GB  primary   ext4            boot
        20,0GB  20,0GB  1048kB            Free Space
 2      20,0GB  500GB   480GB   extended
 5      20,0GB  22,0GB  2047MB  logical   linux-swap(v1)
 6      22,0GB  500GB   478GB   logical   ext4
        500GB   1000GB  500GB             Free Space
```

I rebooted server that /home wont get mounted, that is enough?

With parted I tried to use 'resize' command. (can't copy&paste these)
$ parted /dev/sda resize 6
it asked start size so I kept it default '22,0GB'
it asked end size so i changed it from default '500GB' to 1000GB
after that it gave me 'incompatible feature' error

So how I can grow that partition without losing data?

---

### Post by vanadium on 2011-03-12
You must enlarge the extended partition sda2 first before you can extend the logical partition sda6, which exists in that extended partition.

---

### Post by BkkBonanza on 2011-03-12
If you have physical access and can boot on a live cd I'd suggest using Gparted. It makes it very easy to grow/shrink partitions. It does take it's time though having used it several times it always runs for a long time but for me it has always worked well and the gui interface makes it simple.

---

### Post by 8Kuula on 2011-03-12
Aaaw, extended first...damn im stupid... :D
Thanks, problem solved :)

---

### Post by vanadium on 2011-03-12
> **BkkBonanza said:**
> It does take it's time though having used it several times it always runs for a long time but for me it has always worked well and the gui interface makes it simple.
It should go very fast as long as you do only move the end of the partition. Only when you move the partition, along with resizing, is relocation of the data needed, and that is what takes (a lot of) time, and sometimes without guarantee of a good ending.

---

