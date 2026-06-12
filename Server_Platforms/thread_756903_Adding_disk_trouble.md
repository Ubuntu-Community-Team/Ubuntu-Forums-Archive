---
title: "Adding disk trouble"
date: 2008-04-16
forum: Server Platforms
---

### Post by SpaceCake on 2008-04-16
Hi all,

I have some issues during boot.

Installed Ubuntu server 7,10:
2 scsi hdd
  - sda
     /
     /var
  - sdb  hdd
      swap
      (free space)
Added a SATA DISK (NTFS partition), here the trouble started..

it become sda, and moved scsi disc sda to sdb position ..

**First boot:**
        Boot sequence halted with the last message saying unable to with init ram, or something similar.
RESET

**Second boot:**
    It booted normally !!


> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
UUID=9199d459-5cda-41df-942e-3118d515e163 /               ext3    defaults,errors=remount-ro 0       1
UUID=962ad255-16c1-42b1-9a86-9917199e8dc1 /var            ext3    defaults        0       2
/dev/sdc3       none            swap    sw              0       0
UUID=c29088d7-a4f1-4f30-9655-580857870bab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1       /mnt/sata       fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096        0       0

**mtab**
> /dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0

**grub menu.lst**
> title           Ubuntu 7.10, kernel 2.6.22-14-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-server root=UUID=9199d459-5cda-41df-942e-3118d515e163 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-server


Is it maybe **root (hd0,0)** the issue ?

heeelp,
Space

---

### Post by SpaceCake on 2008-04-18
Anybody ?

sorry for the bump ..

---

