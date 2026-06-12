---
title: "server 11.10 on MS 2008 R2 Hyper V"
date: 2011-11-02
forum: Virtualisation
---

### Post by osl on 2011-11-02
I have setup ubuntu server v 11.10 64bit on a Microsoft Hyper V platform. Since adding the hv_ modules I have two disks sda & hda both of which are the same disk except that sda reports the wrong size. The hyper v setup doesn't have a scsi disk attached and only one 200GB IDE drive.
 
vgdisplay shows duplicate PV:
 
Found duplicate PV wQRvuNRF2HwzcyJGrH59tKXjMYw64ytS: using /dev/sda5 not /dev/hda5
--- Volume group ---
VG Name lewis
System ID
Format lvm2
Metadata Areas 1
Metadata Sequence No 3
VG Access read/write
VG Status resizable
MAX LV 0
Cur LV 2
Open LV 2
Max PV 0
Cur PV 1
Act PV 1
VG Size 127.25 GiB
PE Size 4.00 MiB
Total PE 32577
Alloc PE / Size 30993 / 121.07 GiB
Free PE / Size 1584 / 6.19 GiB
VG UUID yc9uXr-dvHY-mz6I-E0xf-1oTX-e7Hi-bfIUuE
 
fdisk /dev/sda shows:
 
Disk /dev/sda: 136.9 GB, 136899993600 bytes
255 heads, 63 sectors/track, 16643 cylinders, total 267382800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b731d
Device Boot Start End Blocks Id System
/dev/sda1 * 2048 499711 248832 83 Linux
/dev/sda2 501758 267380735 133439489 5 Extended
/dev/sda5 501760 267380735 133439488 8e Linux LVM
 
fdisk /dev/hda shows:
 
Disk /dev/hda: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders, total 419430400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b731d
Device Boot Start End Blocks Id System
/dev/hda1 * 2048 499711 248832 83 Linux
/dev/hda2 501758 267380735 133439489 5 Extended
/dev/hda5 501760 267380735 133439488 8e Linux LVM
 
mount shows:
 
/dev/mapper/lewis-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/hda1 on /boot type ext2 (rw)
 
So you can see sda and hda are the same device. sda has it as 136.9 GB while hda has it as 214.7 GB and hyper v has it as 200GB.
 
Can anyone advise on how to remove sda, why hda is reporting the extra 14.7 GBs and will I have problems if I extend the VG to use the whole 200GB drive?
 
Many Thanks
 
John McAlinden

---

### Post by dcstar on 2011-11-04
> **osl said:**
> I have setup ubuntu server v 11.10 64bit on a Microsoft Hyper V platform. Since adding the hv_ modules I have two disks sda & hda both of which are the same disk except that sda reports the wrong size.
..........
So you can see sda and hda are the same device. sda has it as 136.9 GB while hda has it as 214.7 GB and hyper v has it as 200GB.
 
Can anyone advise on how to remove sda, why hda is reporting the extra 14.7 GBs and will I have problems if I extend the VG to use the whole 200GB drive?
 
Many Thanks
 
John McAlinden

GiB <> GB

---

### Post by mruiz@ic-sa.com on 2012-03-12
> **dcstar said:**
> GiB <> GB

Have you guys got the Seth0 driver to work on Hyper-V.  I have added this.

hv_vmbus
hv_blkvsc
hv_netvsc
hv_utils
hv_storevsc

for the ifconfig i have this

auto seth0
iface seth0 inet static

Any help will be great.

---

