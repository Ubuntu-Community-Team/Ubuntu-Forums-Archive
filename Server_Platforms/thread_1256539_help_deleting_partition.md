---
title: "help deleting partition"
date: 2009-09-02
forum: Server Platforms
---

### Post by erc9003 on 2009-09-02
Hey I have looked around a bit for support with Gparted and fdisk alike, but I cannot seem to find threads relating to my problem.

I am trying to create a Raid1 array using mdadm but one of my disks will not format.  Upon attempting to format with fdisk, I get:

```
skeletor@xxxskull:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
Selected partition 1

Command (m for help): 
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
No partition is defined yet!

Command (m for help): p

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041c9f

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-91201, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-91201, default 91201): 
Using default value 91201

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Using Gparted, I can successfully delete the partition, but when I attempt to create a new one, it barfs:

```
GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext3, 698.64 GiB) on /dev/sdb  00:00:21    ( ERROR )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 1465144064
size: 1465144002 (698.64 GiB)
set partition type on /dev/sdb1  00:00:10    ( SUCCESS )
     	
new partition type: ext3
create new ext3 file system  00:00:00    ( ERROR )
     	
mkfs.ext3 -L "sdb1" /dev/sdb1
     	
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!

========================================
```

Any help is much appreciated.

---

### Post by hessiess on 2009-09-02
How old is the drive? it may be failing.

---

### Post by tgrimley on 2009-09-02
you don't want to be creating a file system on your individual devices... you want to partition each as "fd" instead of 83, and then assemble the raid volume and create a file system on that.

---

### Post by erc9003 on 2009-09-04
> **hessiess said:**
> How old is the drive? it may be failing.

The drives are brand-spanking new.  :(

> **tgrimley said:**
> you don't want to be creating a file system on your individual devices... you want to partition each as "fd" instead of 83, and then assemble the raid volume and create a file system on that.

Ok, so I must first delete the existing partitions, yes? Any insight on why my deletion is failing?

---

### Post by tgrimley on 2009-09-04
this: [http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html](http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html)
and
this: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Save_The_Changes](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Save_The_Changes)

might help you.  It can't re-read the partition table without rebooting, so try the first link.  The second you should read through for some advice on setting up the raid array.  hope that helps

---

### Post by erc9003 on 2009-09-04
> **tgrimley said:**
> this: [http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html](http://www.cyberciti.biz/tips/re-read-the-partition-table-without-rebooting-linux-system.html)
and
this: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Save_The_Changes](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Save_The_Changes)

might help you.  It can't re-read the partition table without rebooting, so try the first link.  The second you should read through for some advice on setting up the raid array.  hope that helps

that second link was super helpful! thanks!

however, i rebooted to try it out, and found it had not mounted.

long story short, cat /proc/mdstat reports:

```
Personalities : [raid1] 
md0 : active raid1 sdc1[1] sdb1[0]
      732571904 blocks [2/2] [UU]
      [=====>...............]  resync = 26.3% (192726400/732571904) finish=118.2min speed=76100K/sec

```

what is it doing, and should I expect this every time I reboot? it is taking very long.

---

### Post by tgrimley on 2009-09-04
Should only rebuild when you replace a drive or the first time (like now)  ~75MB/s isn't too slow for a resync :)

---

### Post by erc9003 on 2009-09-05
well thanks for the help!

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/md0 on /mnt/raid type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
```

I have created directories in the raid so it's safe to say it's working, but it does not show up as a device in my Computer when I browse for it with the GUI. Any ideas on that? Any hope for graphical display of properties? Percent used/free, etc?

---

