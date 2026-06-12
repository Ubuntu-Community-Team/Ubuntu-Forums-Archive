---
title: "Cloned system hitch"
date: 2012-05-11
forum: Server Platforms
---

### Post by gharris999 on 2012-05-11
I've just cloned a functioning Ubuntu 12.04 server system drive (via gddrescue) and successfully booted the clone on identical hardware.  I'm finding that the cloned system has a phantom /dev/sdc and that I'm consistently getting these error messages printing to the terminal:

```
[ 1304.602842] sd 4:0:0:0: [sdc] Asking for cache data failed
[ 1304.602963] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1356.314837] sd 4:0:0:0: [sdc] Asking for cache data failed
[ 1356.319538] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 1408.026705] sd 4:0:0:0: [sdc] Asking for cache data failed
[ 1408.031458] sd 4:0:0:0: [sdc] Assuming drive cache: write through
..etc.

```
I can:

# sudo rm -f /dev/sdc

..but /dev/sdc reappears on subsequent boots.

How do I convince Ubuntu that there is no /dev/sdc?

---

### Post by Jake.Debord on 2012-05-11
Is it mounted anywhere?

---

### Post by gharris999 on 2012-05-11
> **Jake.Debord said:**
> Is it mounted anywhere?

Nope. While # ls -l /dev/sd? returns:

```

# ls -l /dev/sd?
brw-rw---- 1 root disk 8,  0 May 11 10:16 /dev/sda
brw-rw---- 1 root disk 8, 16 May 11 10:17 /dev/sdb
brw-rw---- 1 root disk 8, 32 May 11 10:22 /dev/sdc

```

.. # fdisk -l returns:

```

# fdisk -l

Disk /dev/sda: 64.0 GB, 64030244864 bytes
255 heads, 63 sectors/track, 7784 cylinders, total 125059072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000769ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   120883199    60440576   83  Linux
/dev/sda2       120885246   125057023     2085889    5  Extended
/dev/sda5       120885248   125057023     2085888   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


```

..so you can see that there is no /dev/sdc device (according to fdisk.)

mount -l returns:

```

n# mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb2 on /mnt/EstherMedia3T type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096) [EstherMedia3T]

```
..and blkid returns:

```

n# blkid
/dev/sda1: UUID="08291d37-b6e1-404a-91d3-b6f025125708" TYPE="ext4"
/dev/sda5: UUID="43a34a01-7c75-483e-809c-e1e225e0ab0a" TYPE="swap"
/dev/sdb2: LABEL="EstherMedia3T" UUID="3AE8C525E8C4E06D" TYPE="ntfs"

```

---

### Post by Jake.Debord on 2012-05-11
do you have any usb drives attached?

---

### Post by gharris999 on 2012-05-11
> **Jake.Debord said:**
> do you have any usb drives attached?
Also nope.  I've also uninstalled the usbmount package.

This system is booting off a CF card on /dev/sda.  Even after booting without attaching the SATA data hard disk, the system still thinks there is a phantom 2nd device, now at /dev/sdb.

/var/log/dmesg now contains:

[    3.272668] sd 4:0:0:0: [sdb] Attached SCSI removable disk


..and /var/log/udev contains:

```
KERNEL[7.879809] add      /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/host4/target4:0:0/4:0:0:0/block/sdb (block)
ACTION=add
DEVNAME=sdb
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/host4/target4:0:0/4:0:0:0/block/sdb
DEVTYPE=disk
MAJOR=8
MINOR=16
SEQNUM=1432
SUBSYSTEM=block
UDEV_LOG=3

```

So, just to reiterate, the only attached devices at this point are:

CF card (boot drive)
USB keyboard
USB mouse
VGA monitor
Ethernet cable.

That's it.

Some how, it seems like udev is convinced that something else is attached, though.

---

### Post by Jake.Debord on 2012-05-11
I have a feeling because its a cloned system it's checking that cf card for a cache that isn't there. I bet the other original machine doesn't have that card reader or if it does it's got something to do with that card. I googled it and it looks harmless other than being annoying in the CLI. 

That cf card is showing up as removable disk and causing a hiccup when the system checks the cache of the drives.

---

### Post by gharris999 on 2012-05-11
> **Jake.Debord said:**
> I have a feeling because its a cloned system it's checking that cf card for a cache that isn't there. I bet the other original machine doesn't have that card reader or if it does it's got something to do with that card. I googled it and it looks harmless other than being annoying in the CLI. 

That cf card is showing up as removable disk and causing a hiccup when the system checks the cache of the drives.
The clone is a clone of another CF card.  I.e., two identical systems, hardware-wise, both booting from identical CF cards.

---

### Post by gharris999 on 2012-05-11
I thought that following the instructions of answer #2 here:

[http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled](http://askubuntu.com/questions/132100/errors-in-dmesg-test-wp-failed-assume-write-enabled)

..might have solved the problem...but no.  Still getting the annoying kernel messages on tty1.

---

