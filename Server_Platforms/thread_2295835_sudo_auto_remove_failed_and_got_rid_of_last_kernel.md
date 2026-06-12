---
title: "sudo auto remove failed and got rid of last kernel"
date: 2015-09-21
forum: Server Platforms
---

### Post by gtr@frii.com on 2015-09-21
I had gone through a couple of apt-get updates/upgrades this week on a box running 14.04.3 LTS which got me to (I believe kernel 3.13.0-63-generic).  After each upgrade, I was unable to boot - it hung, usually at mounting swap.  I successfully booted with 3.13.0.61-generic (after the first upgrade) and yesterday (9-21) the same thing happened again.  Today I tried sudo apt-get update/upgrade and after that evolution the system booted successfully (I wasn't paying attention to the release, but assume it was either 3.13.0-63-generic with some related fixes or 3.13.0.64-generic), and told me I had lots of kernels that could be removed.  So, I ran sudo apt-get autoremove. It churned for awhile and then spewed error messages (not finding some .ko files).  I looked in /boot and found 3.13.0.57-generic related files were the only thing still there.  I ran sudo update-grub, which succeeded but told me I could autoremove 3.13.0.57-generic - which I did NOT do.  The system booted successfully on 3.13.0.57-generic.  At that point, I decided to try apt-get installing the linuz image but that quit saying I had the latest image.  When this first happened, I had made copies of the applicable boot files for 3.13.0-62-generic and 3.13.0-63-generic (which wouldn't boot), but unfortunately, not for whatever kernel that successfully booted today before I ran autoremove.  As things stand right now, after updating grub I am running the box on 3.13.0.57-generic, but I think I really should be on a later kernel.  So,.. what is the correct latest kernel for 14.04.3 LTS and how can I get/install it?

---

### Post by Bashing-om on 2015-09-21
[email]gtr@frii.com[/email]; UnGoodl

Let's see what we can find out that might point to the cause:
Post back:
```

dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd*
ls -al /boot/
ls -al /usr/src/
ls -al /lib/modules/

```
Get some light shed
[INDENT][INDENT]on the subject
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-21
```
dpkg -l | grep linux- 
ii  linux-firmware                      1.127.15                         all          Firmware for Linux kernel drivers
ii  linux-generic                       3.13.0.63.71                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-57             3.13.0-57.95                     all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic     3.13.0-57.95                     amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63             3.13.0-63.103                    all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic     3.13.0-63.103                    amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic               3.13.0.63.71                     amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-32-generic       3.13.0-32.57                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-39-generic       3.13.0-39.66                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic       3.13.0-40.69                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic       3.13.0-43.72                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic       3.13.0-44.73                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic       3.13.0-45.74                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic       3.13.0-46.79                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic       3.13.0-48.80                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic       3.13.0-49.83                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic       3.13.0-51.84                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-52-generic       3.13.0-52.86                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic       3.13.0-53.89                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-54-generic       3.13.0-54.91                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic       3.13.0-55.94                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic       3.13.0-57.95                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic       3.13.0-58.97                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic       3.13.0-59.98                     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic       3.13.0-61.100                    amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic       3.13.0-62.102                    amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic       3.13.0-63.103                    amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic 3.13.0-32.57                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-39-generic 3.13.0-39.66                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic 3.13.0-40.69                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic 3.13.0-43.72                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic 3.13.0-44.73                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic 3.13.0-45.74                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic 3.13.0-46.79                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic 3.13.0-48.80                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-49-generic 3.13.0-49.83                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic 3.13.0-51.84                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic 3.13.0-52.86                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic 3.13.0-53.89                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-54-generic 3.13.0-54.91                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic 3.13.0-55.94                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic 3.13.0-57.95                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic 3.13.0-58.97                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic 3.13.0-59.98                     amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic 3.13.0-61.100                    amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic 3.13.0-62.102                    amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic 3.13.0-63.103                    amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                 3.13.0.63.71                     amd64        Generic Linux kernel image
```

```
root@agplatter2:~# ls -al /vmlinuz*
ls: cannot access /vmlinuz*: No such file or directory
```
```
root@agplatter2:~# ls -al /boot/ > second
root@agplatter2:~# cat second
total 29744
drwxr-xr-x  4 root root     4096 Sep 21 16:28 .
drwxr-xr-x 22 root root     4096 Sep 21 16:12 ..
-rw-r--r--  1 root root  1164984 Jun 19 04:04 abi-3.13.0-57-generic
-rw-r--r--  1 root root   165762 Jun 19 04:04 config-3.13.0-57-generic
drwxr-xr-x  5 root root     4096 Sep 21 16:28 grub
-rw-r--r--  1 root root 19344970 Jul  7 06:39 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
drwxr-xr-x  2 root root     4096 Sep 15 21:42 saved
-rw-------  1 root root  3391581 Jun 19 04:04 System.map-3.13.0-57-generic
-rw-------  1 root root  5820800 Jun 19 04:04 vmlinuz-3.13.0-57-generic
root@agplatter2:~# ls -al /usr/src > third
root@agplatter2:~# cat third
total 24
drwxr-xr-x  6 root root 4096 Sep 21 16:12 .
drwxr-xr-x 10 root root 4096 Nov  8  2014 ..
drwxr-xr-x 24 root root 4096 Jul  7 06:37 linux-headers-3.13.0-57
drwxr-xr-x  7 root root 4096 Jul  7 06:37 linux-headers-3.13.0-57-generic
drwxr-xr-x 24 root root 4096 Sep  3 06:55 linux-headers-3.13.0-63
drwxr-xr-x  7 root root 4096 Sep  3 06:55 linux-headers-3.13.0-63-generic
root@agplatter2:~
root@agplatter2:~# ls -al /lib/modules
total 16
drwxr-xr-x  4 root root 4096 Sep 21 16:13 .
drwxr-xr-x 21 root root 4096 Nov  8  2014 ..
drwxr-xr-x  5 root root 4096 Jul  7 06:39 3.13.0-57-generic
drwxr-xr-x  5 root root 4096 Sep  3 06:57 3.13.0-63-generic
root@agplatter2:~#
```

---

### Post by Bashing-om on 2015-09-21
[email]gtr@frii.com[/email]; Well ...

1st up might give high consideration to change your name here on the forum, If this is a valid email the web crawlers are going to spam you to pieces.

OK, as to the current situation:
The symlinks in the "root " (/) directory should exist. Mine for your reference:
```

sysop@1404mini:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Sep  3 14:35 /vmlinuz -> boot/vmlinuz-3.13.0-63-generic
lrwxrwxrwx 1 root root 30 Aug 18 12:07 /vmlinuz.old -> boot/vmlinuz-3.13.0-62-generic
sysop@1404mini:~$ ls -al /initrd*
lrwxrwxrwx 1 root root 33 Sep  3 14:35 /initrd.img -> boot/initrd.img-3.13.0-63-generic
lrwxrwxrwx 1 root root 33 Aug 18 12:07 /initrd.img.old -> boot/initrd.img-3.13.0-62-generic
sysop@1404mini:~$

```


But. but, but .. in your /boot directory you have no -63 kernel installed, though the module and headers files do exist !

Let's try this - before doing any cleanup of residual files and those old kernels marked 'rc'.
See if the -63 kernel will install and make up the required symlink(s) for us:
```

sudo apt-get install --reinstall linux-image-3.13.0-63-generic
sudo apt-get install --reinstall linux-image-extra-3.13.0-63-generic
sudo apt-get install --reinstall linux-headers-3.13.0-63
sudo apt-get install --reinstall linux-headers-3.13.0-63-generic

```

Are the symlinks now established ?

[INDENT][INDENT]it is a process
[INDENT][INDENT][INDENT]point a to point d
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-21
Yes the symlinks for -63 are now established
root@agplatter2:~# ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Sep 21 20:27 /vmlinuz -> boot/vmlinuz-3.13.0-63-generic
root@agplatter2:~# ls -al /initrd*
lrwxrwxrwx 1 root root 33 Sep 21 20:27 /initrd.img -> boot/initrd.img-3.13.0-63-generic
root@agplatter2:~#

---

### Post by Bashing-om on 2015-09-21
[email]gtr@frii.com[/email]; Making progress !

Are you in a position to re-boot and make sure the -63 kernel boots ?

If it does, how 'bout we install the -62 kernel as the backup kernel ?
Chances are we will have to manually set the symlinks for the -62 kernel.

Then we clean things up.

[INDENT][INDENT]who said it could not be done
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-21
It hung during boot:
[15.193882] adding 7853356K swap on /dev/sda5 priority 0a extents=1 across 783356k FS

Rebooted and chose -57 kernel and it booted successfully.
Last login: Mon Sep 21 20:49:56 2015
glensa@agplatter2:~$ uname -a
Linux agplatter2 3.13.0-57-generic #95-Ubuntu SMP Fri Jun 19 09:28:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
glensa@agplatter2:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      114475608 4307708 104329772   4% /
none                   4       0         4   0% /sys/fs/cgroup
udev              368972       8    368964   1% /dev
tmpfs              75968    1104     74864   2% /run
none                5120       0      5120   0% /run/lock
none              379824       0    379824   0% /run/shm
none              102400       0    102400   0% /run/user
glensa@agplatter2:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=2df2cac9-193c-46a0-a0ed-5e761460db06 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=59bb34e1-4e6e-4ee7-b23d-e9e61a69c8e3 none            swap    sw              0       0
glensa@agplatter2:~$ sudo blkid
[sudo] password for glensa: 
/dev/sda1: UUID="2df2cac9-193c-46a0-a0ed-5e761460db06" TYPE="ext4" 
/dev/sda5: UUID="59bb34e1-4e6e-4ee7-b23d-e9e61a69c8e3" TYPE="swap" 
glensa@agplatter2:~$ 
This is the failure to boot scenario that started this exercise.
Should I try removing swap from or ...

one more bit of info (and I could add another physical disk for swap if necessary)
glensa@agplatter2:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063617

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232871935   116434944   83  Linux
/dev/sda2       232873982   234440703      783361    5  Extended
/dev/sda5       232873984   234440703      783360   82  Linux swap / Solaris
glensa@agplatter2:~$

---

### Post by Bashing-om on 2015-09-21
[email]gtr@frii.com[/email]; Well ..

Now, that just does not make a lot of sense.
Let's see what happens when we re-configure that image

Please use code tags for the outputs - read as much 'code' in a days time as we do, it makes a BIG difference. Maintains formatting and supports readability !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo update-initramfs -vu -k 3.13.0-63-generic

```
the -v for verbose mode so it tells us what it is doing, and examine that to see if it gives clues .

As to swap, the UUID's agree, but does the partition exist ?
```

sudo fdisk -lu

```


[INDENT][INDENT]as we look for what is 
[INDENT][INDENT][INDENT]to make it happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-21
```

glensa@agplatter2:~$ sudo update-initramfs -vu -k 3.13.0-63-generic
[sudo] password for glensa: 
Keeping /boot/initrd.img-3.13.0-63-generic.dpkg-bak
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/usbhid/usbhid.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-apple.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-cherry.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/input/ff-memless.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-logitech.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-logitech-dj.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-microsoft.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-a4tech.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-belkin.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-chicony.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-cypress.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-ezkey.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-gyration.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-monterey.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-petalynx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-pl.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-samsung.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-sony.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-sunplus.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-tmff.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-zpff.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hid/hid-generic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/crypto/xor.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/libcrc32c.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/raid6/raid6_pq.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/btrfs/btrfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/isofs/isofs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/jfs/jfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/fscache/fscache.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/sunrpc/sunrpc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/lockd/lockd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/nfs/nfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/nfs_common/nfs_acl.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/nfs/nfsv3.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/nfs/nfsv4.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/reiserfs/reiserfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/crc-itu-t.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/udf/udf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/xfs/xfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/nls/nls_iso8859-1.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/input/mouse/psmouse.ko
Copying module directory kernel/drivers/net
(excluding appletalk arcnet bonding can hamradio irda pcmcia tokenring usb wan wimax wireless)
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/rionet.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/mii.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/macvlan.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/macvtap.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hv/hv_vmbus.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/hyperv/hv_netvsc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/mdio.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/sb1000.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/fs/configfs/configfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/netconsole.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/nlmon.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/dsa/dsa_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/dsa/mv88e6060.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/dsa/mv88e6xxx_drv.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/dummy.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/slip/slip.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/fddi/skfp/skfp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/fddi/defxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/pppox.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/pppoe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/ppp_deflate.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/ppp_synctty.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/ppp_async.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/ppp_mppe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/bsd_comp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/ipv4/gre.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ppp/pptp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team_mode_roundrobin.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team_mode_random.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team_mode_broadcast.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team_mode_loadbalance.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/team/team_mode_activebackup.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/xen-netback/xen-netback.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ifb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sis/sis190.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sis/sis900.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/pps/pps_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ptp/ptp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/ipv4/ip_tunnel.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/vxlan.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_en.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/mellanox/mlx5/core/mlx5_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/xircom/xirc2ps_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/fealnx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/fujitsu/fmvj18x_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sun/sungem.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sun/cassini.ko
Adding firmware /lib/firmware/sun/cassini.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sun/sunhme.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sun/niu.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/hp/hp100.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/via/via-velocity.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/via/via-rhine.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mtd/mtd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/sfc/sfc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/chelsio/cxgb4/cxgb4.ko
Adding firmware /lib/firmware/cxgb4/t5fw.bin
Adding firmware /lib/firmware/cxgb4/t4fw.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/chelsio/cxgb/cxgb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/chelsio/cxgb3/cxgb3.ko
Adding firmware /lib/firmware/cxgb3/ael2020_twx_edc.bin
Adding firmware /lib/firmware/cxgb3/ael2005_twx_edc.bin
Adding firmware /lib/firmware/cxgb3/ael2005_opt_edc.bin
Adding firmware /lib/firmware/cxgb3/t3c_psram-1.1.0.bin
Adding firmware /lib/firmware/cxgb3/t3b_psram-1.1.0.bin
Adding firmware /lib/firmware/cxgb3/t3fw-7.12.0.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/chelsio/cxgb4vf/cxgb4vf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/dca/dca.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/myricom/myri10ge/myri10ge.ko
Adding firmware /lib/firmware/myri10ge_rss_eth_z8e.dat
Adding firmware /lib/firmware/myri10ge_rss_ethp_z8e.dat
Adding firmware /lib/firmware/myri10ge_eth_z8e.dat
Adding firmware /lib/firmware/myri10ge_ethp_z8e.dat
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/microchip/enc28j60.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/stmicro/stmmac/stmmac.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/silan/sc92031.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/neterion/vxge/vxge.ko
Adding firmware /lib/firmware/vxge/X3fw.ncf
Adding firmware /lib/firmware/vxge/X3fw-pxe.ncf
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/neterion/s2io.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/smsc/smsc9420.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/smsc/epic100.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/smsc/smc91c92_cs.ko
Adding firmware /lib/firmware/ositech/Xilinx7OD.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/smsc/smsc911x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/tehuti/tehuti.ko
Adding firmware /lib/firmware/tehuti/bdx.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/micrel/ks8851.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/micrel/ksz884x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/micrel/ks8851_mll.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/micrel/ks8842.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/qlogic/netxen/netxen_nic.ko
Adding firmware /lib/firmware/phanfw.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/qlogic/qla3xxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/qlogic/qlge/qlge.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/qlogic/qlcnic/qlcnic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/broadcom/bnx2.ko
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2/bnx2-rv2p-09-6.0.17.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2/bnx2-mips-09-6.2.1b.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2/bnx2-rv2p-06-6.0.15.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2/bnx2-mips-06-6.2.3.fw
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/broadcom/b44.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/broadcom/bnx2x/bnx2x.ko
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2x/bnx2x-e2-7.8.17.0.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2x/bnx2x-e1h-7.8.17.0.fw
Adding firmware /lib/firmware/3.13.0-63-generic/bnx2x/bnx2x-e1-7.8.17.0.fw
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko
Adding firmware /lib/firmware/3.13.0-63-generic/tigon/tg3_tso5.bin
Adding firmware /lib/firmware/3.13.0-63-generic/tigon/tg3_tso.bin
Adding firmware /lib/firmware/3.13.0-63-generic/tigon/tg3.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/wiznet/w5300.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/wiznet/w5100.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/icplus/ipg.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/amd/pcnet32.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/amd/amd8111e.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/amd/nmclan_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/3com/3c589_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/3com/3c59x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/3com/typhoon.ko
Adding firmware /lib/firmware/3.13.0-63-generic/3com/typhoon.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/3com/3c574_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/8390/8390.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/8390/ne2k-pci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/8390/axnet_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/8390/pcnet_cs.ko
Adding firmware /lib/firmware/cis/tamarack.cis
Adding firmware /lib/firmware/cis/PE-200.cis
Adding firmware /lib/firmware/cis/NE2K.cis
Adding firmware /lib/firmware/cis/PE520.cis
Adding firmware /lib/firmware/cis/LA-PCM.cis
Adding firmware /lib/firmware/cis/DP83903.cis
Adding firmware /lib/firmware/cis/PCMLM28.cis
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/natsemi/ns83820.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/natsemi/natsemi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/emulex/benet/be2net.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/brocade/bna/bna.ko
Adding firmware /lib/firmware/ct2fw-3.2.1.1.bin
Adding firmware /lib/firmware/ctfw-3.2.1.1.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/dmfe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/xircom_cb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/uli526x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/winbond-840.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/de2104x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/de4x5.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dec/tulip/tulip.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/jme.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/ethoc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/packetengines/hamachi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/packetengines/yellowfin.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/apm/xgene/xgene-enet.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/cadence/macb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/cadence/at91_ether.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/calxeda/xgmac.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/igbvf/igbvf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/e100.ko
Adding firmware /lib/firmware/3.13.0-63-generic/e100/d102e_ucode.bin
Adding firmware /lib/firmware/3.13.0-63-generic/e100/d101s_ucode.bin
Adding firmware /lib/firmware/3.13.0-63-generic/e100/d101m_ucode.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/i40evf/i40evf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/e1000/e1000.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/ixgb/ixgb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/ixgbevf/ixgbevf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/igb/igb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/i40e/i40e.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/ti/tlan.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/atheros/atlx/atl1.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/atheros/atlx/atl2.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/atheros/atl1e/atl1e.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/renesas/sh_eth.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/cisco/enic/enic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/rdc/r6040.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/realtek/8139cp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
Adding firmware /lib/firmware/rtl_nic/rtl8168g-3.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168g-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8106e-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8106e-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8411-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8411-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8402-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168f-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168f-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8105e-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168e-3.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168e-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168e-1.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168d-2.fw
Adding firmware /lib/firmware/rtl_nic/rtl8168d-1.fw
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/realtek/8139too.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/realtek/atp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dnet.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dlink/dl2k.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/dlink/sundance.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/adaptec/starfire.ko
Adding firmware /lib/firmware/adaptec/starfire_tx.bin
Adding firmware /lib/firmware/adaptec/starfire_rx.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/alteon/acenic.ko
Adding firmware /lib/firmware/acenic/tg2.bin
Adding firmware /lib/firmware/acenic/tg1.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/marvell/mvmdio.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/marvell/skge.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/marvell/sky2.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ptp/ptp_pch.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ethernet/oki-semi/pch_gbe/pch_gbe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/plip/plip.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/ieee802154/ieee802154.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/mac802154/mac802154.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ieee802154/at86rf230.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ieee802154/fakelb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ieee802154/mrf24j40.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ntb/ntb.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/ntb_netdev.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/phy/spi_ks8995.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/caif/cfspi_slave.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/caif/caif_hsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/vhost/vringh.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/caif/caif_virtio.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/caif/caif_serial.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/net/veth.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/device_handler/scsi_dh.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/hv_storvsc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding firmware /lib/firmware/ql2500_fw.bin
Adding firmware /lib/firmware/ql2400_fw.bin
Adding firmware /lib/firmware/ql2322_fw.bin
Adding firmware /lib/firmware/ql2300_fw.bin
Adding firmware /lib/firmware/ql2200_fw.bin
Adding firmware /lib/firmware/ql2100_fw.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/target/target_core_mod.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/qla2xxx/tcm_qla2xxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/iscsi_boot_sysfs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/virtio_scsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/megaraid/megaraid_sas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/mpt3sas/mpt3sas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/bnx2fc/bnx2fc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/qla1280.ko
Adding firmware /lib/firmware/3.13.0-63-generic/qlogic/12160.bin
Adding firmware /lib/firmware/3.13.0-63-generic/qlogic/1280.bin
Adding firmware /lib/firmware/3.13.0-63-generic/qlogic/1040.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/bfa/bfa.ko
Adding firmware /lib/firmware/cbfw-3.2.1.1.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/advansys.ko
Adding firmware /lib/firmware/advansys/38C1600.bin
Adding firmware /lib/firmware/advansys/38C0800.bin
Adding firmware /lib/firmware/advansys/3550.bin
Adding firmware /lib/firmware/advansys/mcode.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/esas2r/esas2r.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/3w-sas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/csiostor/csiostor.ko
Adding firmware /lib/firmware/cxgb4/t5fw.bin
Adding firmware /lib/firmware/cxgb4/t4fw.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/isci/isci.ko
Adding firmware /lib/firmware/isci/isci_firmware.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/mvumi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ufs/ufshcd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ufs/ufshcd-pci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/ufs/ufshcd-pltfrm.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pm8001/pm80xx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pmcraid.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/hpsa.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/null_blk.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/net/ceph/libceph.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/rbd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/skd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/rsxx/rsxx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/cciss.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/lru_cache.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/drbd/drbd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/nvme.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/block/osdblk.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_piccolo.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/libahci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/phy/phy-core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/ahci_platform.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/acard-ahci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pdc_adma.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_rcar.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_arasan_cf.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_acpi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/ata/pata_platform.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/firewire/firewire-sbp2.ko
Copying module directory kernel/drivers/mmc
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/card/mmc_block.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/card/sdio_uart.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/misc/cb710/cb710.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/cb710-mmc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdricoh_cs.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/vub300.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mfd/rtsx_pci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/wbsd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci-pxav3.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci-acpi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci-pxav2.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/via-sdmmc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/ushc.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/misc/tifm_core.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/tifm_sd.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/lib/crc7.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/mmc_spi.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/mmc/host/sdhci-pci.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-realtek.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-eneub6250.ko
Adding firmware /lib/firmware/ene-ub6250/ms_rdwr.bin
Adding firmware /lib/firmware/ene-ub6250/msp_rdwr.bin
Adding firmware /lib/firmware/ene-ub6250/ms_init.bin
Adding firmware /lib/firmware/ene-ub6250/sd_rdwr.bin
Adding firmware /lib/firmware/ene-ub6250/sd_init2.bin
Adding firmware /lib/firmware/ene-ub6250/sd_init1.bin
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/3.13.0-63-generic/kernel/drivers/hv/hv_utils.ko
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/x86_64-linux-gnu/libudev.so.1
Adding library /lib/x86_64-linux-gnu/libc.so.6
Adding library /lib/x86_64-linux-gnu/libcgmanager.so.0
Adding library /lib/x86_64-linux-gnu/libnih.so.1
Adding library /lib/x86_64-linux-gnu/libnih-dbus.so.1
Adding library /lib/x86_64-linux-gnu/libdbus-1.so.3
Adding library /lib/x86_64-linux-gnu/librt.so.1
Adding library /lib64/ld-linux-x86-64.so.2
Adding library /lib/x86_64-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/x86_64-linux-gnu/libblkid.so.1
Adding library /lib/x86_64-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/x86_64-linux-gnu/libext2fs.so.2
Adding library /lib/x86_64-linux-gnu/libcom_err.so.2
Adding library /lib/x86_64-linux-gnu/libe2p.so.2
Calling hook fuse
Adding binary /sbin/mount.fuse
Calling hook klibc
Calling hook kmod
Adding binary /bin/kmod
Calling hook mountall
Calling hook thermal
Calling hook udev
Adding binary /lib/systemd/systemd-udevd
Adding library /lib/x86_64-linux-gnu/libselinux.so.1
Adding library /lib/x86_64-linux-gnu/libkmod.so.2
Adding library /lib/x86_64-linux-gnu/libacl.so.1
Adding library /lib/x86_64-linux-gnu/libpcre.so.3
Adding library /lib/x86_64-linux-gnu/libdl.so.2
Adding library /lib/x86_64-linux-gnu/libattr.so.1
Adding binary /bin/udevadm
Adding binary /lib/udev/ata_id
Adding binary /lib/udev/scsi_id
Calling hook ntfs_3g
Adding binary /bin/ntfs-3g
Adding library /lib/x86_64-linux-gnu/libfuse.so.2
Adding library /lib/x86_64-linux-gnu/libntfs-3g.so.841
Calling hook console_setup
Calling hook kbd
Adding binary /bin/setfont
Adding binary /bin/kbd_mode
Adding binary /bin/loadkeys
Calling hook busybox
Adding binary /usr/lib/initramfs-tools/bin/busybox
Calling hook dmsetup
Adding binary /sbin/dmsetup
Adding library /lib/x86_64-linux-gnu/libdevmapper.so.1.02.1
Calling hook biosdevname
Adding binary /sbin/biosdevname
Adding library /lib/x86_64-linux-gnu/libpci.so.3
Adding library /lib/x86_64-linux-gnu/libz.so.1
Adding library /lib/x86_64-linux-gnu/libresolv.so.2
rm -f ./lib/firmware/cxgb4/t5fw.bin 
rm -f ./lib/firmware/cxgb4/t4fw.bin 
Building cpio /boot/initrd.img-3.13.0-63-generic.new initramfs
glensa@agplatter2:~$

```

```

glensa@agplatter2:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063617

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232871935   116434944   83  Linux
/dev/sda2       232873982   234440703      783361    5  Extended
/dev/sda5       232873984   234440703      783360   82  Linux swap / Solaris
glensa@agplatter2:~$ 

```

---

### Post by Bashing-om on 2015-09-21
[email]gtr@frii.com[/email]; hey ;

That looks to have gone well.
And the swap partition looks good to me also.

Rebooted ? does the -63 kernel boot ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-22
It did not boot.  Had to boot -57.  Thought (totally off the wall) since it was fairly old and not server quality hardware, that maybe there was a bad block in the swap area (because it always hung while mounting the swap partition) that I'd change disks.  Used clonezilla and transferred the disk to a 500 G sata drive.  Rebooted and got exactly the same behavior.  That is, the -63 kernel boot hangs when turning swap on.  The -57 kernel boots just fine. (I did, in fact have the older 120G drive unplugged) with the new disk.  Ideas?

Prior to the initial post, i.e., before doing the autoremove, I was successfully booting with -61 kernel but not with -62 or -63.  Did something major change in the boot sequence at that time (-62)?  Should I try reinstalling -61 kernel and try it?  The running system, which is my home dns/dhcp/nfs/samba server and firewall is currently
up and running (I'm posting from a macbook on wireless through it) seems to be stable, though dmesg is filled with IPV4 martian source messages and net_ratelimit: 5 callbacks suppressed messages.  Do not know if that is relevant (these are all on the dsl modem (internet) attached network card.  I am doing most of the tests over ssh which is going through the local attached network card.   I use a console, interrupting grub, to boot the -57 kernel.

---

### Post by darkod on 2015-09-22
You can also try upgrading/installing the lts enablement stack. That gives you kernel 3.19 for 14.04. As you noticed, unless you do this action manually, the basic kernel still stays 3.13 all the time.

To install 3.19 on 14.04 server try:
```
sudo apt-get install --install-recommends linux-generic-lts-vivid
```

That should give you the latest 3.19 like 3.19.0-28 or something. After that you can see if that boots OK.

PS. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Bashing-om on 2015-09-22
[email]gtr@frii.com[/email]; darkod;

We all have the same thought, though rather than the vivid Xstack, I had in mind to install the -61 kernel.  Yes there is that possibility that with changes in the -62/63 version kernels, something(s) are no longer compatible with your hardware.

Before we go farther, how about we run an update on grub, see if grub reports/has any problems ?
```

sudo update-grub

```
And wont take but seconds to "see" if the system reports any errors in the log files.
```

grep --ignore-case err /var/log/dmesg

grep EE /var/log/Xorg.0.log

``` just to preclude hard drive problems.

Before we get real hot and bothered, let's get 2 kernels installed with their symlinks established in '/' and booting. Just as a safety net.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-22
```

glensa@agplatter2:~$ sudo update-grub
[sudo] password for glensa: 
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

```

glensa@agplatter2:~$ grep --ignore-case err /var/log/dmesg
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.111241] ACPI: Using IOAPIC for interrupt routing
[    0.129633] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.130415] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.131195] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.131977] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.132728] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.133626] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.135766] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.136683] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   11.112084] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.466980] EDAC MC0: Giving out device to module amd64_edac controller K8: DEV 0000:00:18.2 (INTERRUPT)
glensa@agplatter2:~$

```

As an aside, I did try installing the vivid Xstack. and got the same hang. Looking at the console (and writing down most of the stuff based on a couple of boot tries
```

[6.xxxxxx] random: nonblocking pool is initialized
[7.xxxxxx] init. plymouth-upstart-bridge main process (159) terminated with status 1
[7.xxxxxx] init: plymouth upstart-bridge main process ended, responding
[8.xxxxxx] Adding 783345K swap on /dev/sda5 Priority :-1 extents:1 across:783356K FS
[11.xxxxx] MPU-401 device not found or device busy
Hang

```

I installed -61 and can boot from either it or 57, the box is currently up running -61

---

### Post by Bashing-om on 2015-09-22
[email]gtr@frii.com[/email] Humm ...

I gotta think about this sloppyation. Could be we have a bug. Gonna go look about.

[INDENT][INDENT]look'n to blame elsewhere
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-09-23
[email]gtr@frii.com[/email]; Morning;

Sad to say on my part; I am unable to explain why the -62+ kernels do not boot on your system. I will continue to see what I can learn, but presently I am stuck.

[INDENT][INDENT]an opportunity for the learning
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-23
Okay, thanks for your help so far.

---

### Post by Bashing-om on 2015-09-24
[email]gtr@frii.com[/email]; Welp ...

In my pursuit to comprehend where the failure may lie, my google-fu is failing me .

I am hesitant to start a long drawn-out process of discovery. Would be tedious to attempt to boot the later kernels, and start reading the system's various logs in an endeavor to find the fault(s). I would accept that the failure(s) occur before logging is even enabled.

To this time, I do continue - I have found no better instruction as to a cause of failure to boot newer kernels. Maybe it is that the newer kernels have an Xserver stack that no longer supports older hardware ?  Proprietary drivers ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-25
Tried booting -63 kernel with --debug flag, mainly to see if debug would either get relevant messages or slow things down/change order such that boot would succeed.  It always hung.  Basically 2 scenarios.  in one scenario
```

fixing recursive fault but reboot is needed
(paused here for awhile) 
Then scrolled off a stack trace to fast to record but saw something about ATI Radeon
Left on the screen was a couple of page faults
a slow semaphore path
then hang

```
The other predominant failure also included a stack trace (portion of which follows)
```

mutex lock 0x1f/0x2f
radeon_hotplug_work_func 0x26/0x80 [radeon]
some thread trace info
return from fork
thread_create_on_node 0x1c0/0x1c0
[end trace]
perf samples too long (70828>25000) lowering kernel_perf_event_max_sample_rate to 50000
info: nmi handler (perf_event_mi_handler) took to long to run: 9.147 mess
perf samples too long (70278>50000) lowering kernel_perf_event_max_sample_rate to 25000
perf samples too long (69732>10000) lowering kernel_perf_event_max_sample_rate to 12500
perf samples too long (69189>20000) lowering kernel_perf_event_max_sample_rate to 6250
perf samples too long (68650>40000) lowering kernel_perf_event_max_sample_rate to 3250
hang

```
Obviously the numbers changed a bit on subsequent tries but essentially the same.
I am not sure what the debug messages mean, however, it seems strange that on one hand it says it is lowering the sample rate approximately by half while at the same time the test pass value seems to be doubling.  That seems kind of counter intuitive.

In any case, the system seems to be running okay with the -61 kernel.  This has been a pretty solid server, though the hardware is getting old/out of date.  If I don't find an answer/fix, guess I'll have to update hardware for the next LTS.

---

### Post by Bashing-om on 2015-09-25
[email]gtr@frii.com[/email]; Hey !

I am of two thoughts on this.
1) Let's look at what the graphics situation is:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display
X -version
cat /var/log/Xorg.0.log

```
Maybe updating the pciids data base might be of effect ?

I too fall into this category of old hardware .. I run a 2007 dual core AMD Athlon cpu with Non-oem support for the ATI graphic's driver. So far so well for me. I am concerned that I will have to build a new box, but for now 15.04 still runs well.

2) Maybe we can purge the non functional kernels ( images and headers ) as well as the presently installed linux-generic linux-image-generic meta packages. (RE-)install "linux-generic linux-image-generic" and see if that re-install of the meta packages will also pull in the latest -63 kernel and it then be functional ?

[INDENT][INDENT][INDENT]when I know better I do better
[/INDENT][/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-25
```

glensa@agplatter2:~$ lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV100 [Radeon 7000 / Radeon VE] [1002:5159]
	Subsystem: Tul Corporation / PowerColor Device [148c:2072]
	Kernel driver in use: radeon
glensa@agplatter2:~$ sudo lshw -C display
PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: RV100 [Radeon 7000 / Radeon VE]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:e0000000-e7ffffff ioport:a800(size=256) memory:ff5f0000-ff5fffff memory:ff5c0000-ff5dffff
glensa@agplatter2:~$ X -version
The program 'X' is currently not installed. You can install it by typing:
sudo apt-get install xserver-xorg
glensa@agplatter2:~$ cat /var/log/Xorg.0.log
cat: /var/log/Xorg.0.log: No such file or directory
glensa@agplatter2:~$

```

I'll try reinstall and post response afterwards

---

### Post by gtr@frii.com on 2015-09-25
After purging non working kernels and reinstalling generic meta packages the behavior is still the same.  -61 boots and works, -63 hangs and booting debug ends up with the nmi/perf handler hang described in my earlier post.  That is, it appears that there are to many perf/nmi events and from the printed messages the  kernel is attempting to handle that by half'ng the sample rate while doubling the required pass count.  After 3 cycles of that test it appears to give up with kernel_perf_event_max_sample rate set at 3250 and with samples ~70000 >40000.

Server is up and running on -61 kernel

---

### Post by gtr@frii.com on 2015-09-25
Looking/searching mmi/perf it appears that there are some security related issues on nested mmi's particularly on x64 and some code changes were made.  This may be a red herring, but perhaps some combination of upstart and my hardware is leading into nested mmi issues.  

As a completely, off the wall, thought. How hard is it (and is it possible) to change a system from x64 to 686 while keeping modified configuration files?  I have quite a bit of custom stuff for this server (dns caching server, dhcp server, nfs server, samba server,...) and I'd just as soon not start from a clean install if possible.  That path to see if it is only an issue with x64 kernel code.  I realize that ultimately, if this is a hardware corner case issue, I'll have to bite the bullet at some point with new hardware.

---

### Post by gtr@frii.com on 2015-09-25
Looking/searching mmi/perf it appears that there are some security related issues on nested mmi's particularly on x64 and some code changes were made.  This may be a red herring, but perhaps some combination of upstart and my hardware is leading into nested mmi issues.  

As a completely, off the wall, thought. How hard is it (and is it possible) to change a system from x64 to 686 while keeping modified configuration files?  I have quite a bit of custom stuff for this server (dns caching server, dhcp server, nfs server, samba server,...) and I'd just as soon not start from a clean install if possible.  That path to see if it is only an issue with x64 kernel code.  I realize that ultimately, if this is a hardware corner case issue, I'll have to bite the bullet at some point with new hardware.

---

### Post by Bashing-om on 2015-09-25
[email]gtr@frii.com[/email]; Yuk !

I was grasping at straws, and had not considered there would be no ' X ' nor as a consequence a ' /var/log/Xorg.0.log' .

As to graphics; confirmed that ATI no longer supports that card in linux, the only driver option is what you have .

As to the newer kernel install, I am back to spinning my wheels and cogitating what else we might do, or what.
Perhaps in the meantime, someone else with the smarts and experience will come up with a suggestion on how to move this issue forward.

[INDENT][INDENT]gonna have to screw my learning cap 
[INDENT][INDENT][INDENT]on tighter
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gtr@frii.com on 2015-09-25
Since, I have 2 separate disks (I earlier cloned the system disk).  I think, I'll go ahead and migrate one of them to 686 (mounting the other disk after boot to get the modified files easily) and see what that yields.  I'll probably make that attempt tomorrow.

---

### Post by gtr@frii.com on 2015-09-27
The box boots with the latest i686, but at the moment I'm having issues with installing isc-dhcp-server (in another forum) and until I get that solved, I can't go much further.  The box is currently running on x64 -57-generic kernel, so that I have access on my local lan.  It is fairly easy to get to either OS, however, it require I be at the console to interrupt boot.  In other words, if someone has a suggestion, I will try it.

---

### Post by gtr@frii.com on 2015-10-03
Box ran fine on i686 - 14.04.3 LTS kernel 3-19.0-25.  Decided to try vivid LTS so upgraded to 3-19.0-30.  It hung with exactly the same issues as previously on the x64 kernels post -61.  So, ... I'm currently running on i686 3-19.0-25 kernel.  Anyone have ideas as to what I should do next.  The box has 2 disks in it: The disk I am booting from has i686 kernels; the second disk has x64 kernels; one of which will boot in each case.  I am willing to take troubleshooting directions for either/both i686 or x64 kernels.

---

### Post by Bashing-om on 2015-10-03
[email]gtr@frii.com[/email]; Hey !

I wish I had the skills to dissect the kernels to isolate the change.
I do not; will have to leave it to others to take this matter in their hands.

[INDENT][INDENT]donning my learning cap
[/INDENT][/INDENT]

---

