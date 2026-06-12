---
title: "Ubunutu Server 12.04 stucks on boot with lvm on root"
date: 2012-10-08
forum: Server Platforms
---

### Post by kodiakz on 2012-10-08
Hi there,

on boot I can see the error message on 12.04 64bit, with drops into initramfs shell.

```

ALERT! /dev/mapper/server-root does not exist. Dropping to a shell

```

If I do a restart here, the system boots as expected. dmesg shows me then on the booted server:

```

..
[    1.052576] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[    1.053052] EXT4-fs (dm-1): write access will be enabled during recovery
[    1.124048] Refined TSC clocksource calibration: 2533.331 MHz.
[    2.074898] EXT4-fs (dm-1): recovery complete
[    2.182202] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   11.828779] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.994516] udevd[460]: starting version 175
[   12.028275] Adding 983036k swap on /dev/mapper/server-swap.  Priority:-1 extents:1 across:983036k 
[   12.218255] lp: driver loaded but no devices found
[   12.364920] piix4_smbus 0000:00:01.3: SMBus Host Controller at 0xb100, revision 0
[   12.863589] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[   13.389586] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
..

```

my Server has the following partition layout:

```

# fdisk -l

Disk /dev/vda: 21.5 GB, 21474836480 bytes
16 heads, 63 sectors/track, 41610 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a569

   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048      499711      248832   83  Linux
/dev/vda2          501758    41940991    20719617    5  Extended
/dev/vda5          501760    41940991    20719616   8e  Linux LVM

```

and LVM on root

```

# lvdisplay
  --- Logical volume ---
  LV Name                /dev/server/root
  VG Name                server
  LV UUID                xhlIAa-rWw8-VlfT-YwJY-cRgb-OP7L-3XDVKQ
  LV Write Access        read/write
  LV snapshot status     source of
                         /dev/server/snaproot [active]
  LV Status              available
  # open                 1
  LV Size                15.10 GiB
  Current LE             3865
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/server/swap
  VG Name                server
  LV UUID                uL8pej-Yogw-OPjC-kBQ6-QPeC-dXpa-vucgSC
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                960.00 MiB
  Current LE             240
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Logical volume ---
  LV Name                /dev/server/snaproot
  VG Name                server
  LV UUID                ZM3YKY-7SXu-jO48-5Dya-Hx8i-3DBA-3ieTu2
  LV Write Access        read/write
  LV snapshot status     active destination for /dev/server/root
  LV Status              available
  # open                 2
  LV Size                15.10 GiB
  Current LE             3865
  COW-table size         3.72 GiB
  COW-table LE           953
  Allocated to snapshot  31.10% 
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3

```

```

# vgdisplay 
  --- Volume group ---
  VG Name               server
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  55
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               19.76 GiB
  PE Size               4.00 MiB
  Total PE              5058
  Alloc PE / Size       5058 / 19.76 GiB
  Free  PE / Size       0 / 0   
  VG UUID               lhePcx-HQYi-26wC-wNoM-pW6e-DMv6-HzUHYf

```

```

# ll /dev/mapper/
total 0
drwxr-xr-x  2 root root     160 Oct  8 12:31 ./
drwxr-xr-x 14 root root    4060 Oct  8 22:51 ../
crw-------  1 root root 10, 236 Oct  8 12:31 control
lrwxrwxrwx  1 root root       7 Oct  8 12:31 server-root -> ../dm-1
lrwxrwxrwx  1 root root       7 Oct  8 12:31 server-root-real -> ../dm-0
lrwxrwxrwx  1 root root       7 Oct  8 12:31 server-snaproot -> ../dm-3
lrwxrwxrwx  1 root root       7 Oct  8 12:31 server-snaproot-cow -> ../dm-2
lrwxrwxrwx  1 root root       7 Oct  8 12:31 server-swap -> ../dm-4

```


So this behaviour started a few month ago. I can not really tell when it did, since my server is normally up 24/7.

Another interesting thing. If I run..
```

# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /memtest86+.bin
rmdir: failed to remove `/var/lib/os-prober/mount': Device or resource busy
grub-probe: error: unknown filesystem.
done

```

```

# cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.2.0-31-generic root=/dev/mapper/server-root ro

```

What is wrong with it? Any hint is very much appreciate!

---

### Post by kodiakz on 2012-10-09
*bump

---

### Post by kodiakz on 2012-10-10
Solved finally by myself: may qbe related to [ttps://bugs.launchpad.net/ubuntu/+source/grub2/+bug/988583]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/988583") - a least it gave me the hint it was my snapshot. So I removed it and finally I could run update-grub. Rebooting works again.

---

