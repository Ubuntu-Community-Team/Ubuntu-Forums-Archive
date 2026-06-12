---
title: "unable to mount new storage"
date: 2011-08-24
forum: Server Platforms
---

### Post by yud_ on 2011-08-24
I'm a newby, please be gentle on me...

my 11.04 installation is running beautifully in VM on ESXi. I'm trying to add storage so I added the disks, assigned them in vmware to the vm, then tried to mount them when I received the error:
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
         missing codepage or helper program, or other error
         In some cases useful info is found in syslog - try
         dmesg | tail  or so

```dmesg | tail gives:
```

EXT3-fs (sdb1): error: no journal found. mounting ext3 over ext2?

```I tried creating the new partition on the new disks in both webmin and CLI using fdisk but got exactly same errors above when trying to mount. The partition is formatted as ext3.

my setup:
HP Microserver, booting vmware from USB drive. Hardware RAID card (Adaptec RAID 2405), 2 x 250GB HDD in RAID1 (datastore1) with VM's, 2 x 2TB HDD in RAID1 (datastore2) - the storage I'm trying to add.

A search of the above errors yielded many results, all of them were different scenarios to mine.

Any help will be highly appreciated.

Y.

---

### Post by Wayne_V on 2011-08-24
did you create a new file system on the new partitions as well?    see 'man mkfs.ext3' or 'man mkfs.ext4'.  or, you can use the gui:  System->Administration->Disk Utility on Ubuntu 10.04.

---

### Post by yud_ on 2011-08-24
thanks for your reply.
yes, I created ext3 file system.

output of fdisk -l 

```

Disk /dev/sda: 12.9 GB, 12884901888 bytes
255 heads, 63 sectors/track, 1566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e058d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1567    12331009    5  Extended
/dev/sda5              32        1567    12331008   8e  Linux LVM

Disk /dev/sdb: 1990.1 GB, 1990116046848 bytes
255 heads, 63 sectors/track, 241951 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ae0d

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1               1      241952  1943471104   83  Linux**

Disk /dev/dm-0: 10.5 GB, 10477371392 bytes
255 heads, 63 sectors/track, 1273 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 2147 MB, 2147483648 bytes
255 heads, 63 sectors/track, 261 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

```any suggestions?

thanks!

Y.

---

### Post by Wayne_V on 2011-08-25
what is the output of:

sudo fsck -y /dev/sdb1

you could try to reinit the fs again:

sudo mke2fs -t ext3 (or ext4) /dev/sdb1
sudo mount /dev/sdb1 /<mount point>

---

### Post by yud_ on 2011-08-25
Thank you!
reinit the fs resolved the issue and the new partition is now mounted.

Do I now need to add it to fstab?

thanks again.

Y.

---

### Post by Wayne_V on 2011-08-25
great!  yes, if you want it to mount automatically at boot you should add it to fstab.

---

### Post by yud_ on 2011-08-25
can you confirm that this is what I need to put in /etc/fstab:

/dev/sdb1 /<mount point>    ext3   defaults    0    0

(last time I did this the machine stopped booting and I had to revert to a previous snapshot...)

thanks heaps!

Y.

---

### Post by Wayne_V on 2011-08-26
I would tweak that a little:

/dev/sdb1   /<mount point>      ext3   errors=remount-ro      0       2

for the last item:


The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.


If you ever mess anything up here that prevents booting you can always boot recovery mode from the CD to fix it.

---

### Post by yud_ on 2011-08-27
Thank you!

---

