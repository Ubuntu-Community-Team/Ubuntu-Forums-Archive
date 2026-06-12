---
title: "Can't install or upgrade package since rebooting server"
date: 2018-09-28
forum: Server Platforms
---

### Post by launchpad-mfraz on 2018-09-28
I have a server on 16.04 which hasn't been rebooted for about a year. Decided to reboot today as I was planning on upgrading to 18.04 and/or adding another drive.

It rebooted OK, but now when I try to do an update or install a new package it fails:

```
sudo apt dist-upgrade           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up linux-image-4.4.0-133-generic (4.4.0-133.159) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-133.159 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-133.159 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-133-generic /boot/vmlinuz-4.4.0-133-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-133-generic /boot/vmlinuz-4.4.0-133-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-133-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-133-generic /boot/vmlinuz-4.4.0-133-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-133-generic /boot/vmlinuz-4.4.0-133-generic
Generating grub configuration file ...
grub-probe: error: not a directory.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-133-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-133-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-133-generic:
 linux-image-extra-4.4.0-133-generic depends on linux-image-4.4.0-133-generic; however:
  Package linux-image-4.4.0-133-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-133-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-4.4.0-72-generic (4.4.0-72.93) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-72-generic /boot/vmlinuz-4.4.0-72-generic
Generating grub configuration file ...
grub-probe: error: not a directory.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-72-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-4.4.0-133-generic
 linux-image-extra-4.4.0-133-generic
 linux-image-extra-4.4.0-72-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Also, when I do sudo update-grub2
I get:
```
Generating grub configuration file ...
grub-probe: error: not a directory.

fdisk -l             
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x31337774

Device     Boot     Start       End  Sectors Size Id Type
/dev/sda1  *         2048  52430847 52428800  25G 83 Linux
/dev/sda2        52430848 146802687 94371840  45G 83 Linux
/dev/sda3       226045952 234434559  8388608   4G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000a6450

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1        2048 1953519615 1953517568 931.5G 83 Linux


Disk /dev/sdc: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C83B893E-503E-43F1-B506-278DE51B5F0A

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.7T Linux filesystem


Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 056EB2D4-6E3D-43C1-8DA9-6972015443BE

Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 3907022847 3907020800  1.8T Linux filesystem
```

---

### Post by launchpad-mfraz on 2018-09-28
```
sudo grub-probe -v -d /dev/sda1
grub-probe: info: adding `hd0' -> `/dev/sda' from device.map.
grub-probe: info: adding `hd1' -> `/dev/sdb' from device.map.
grub-probe: info: adding `hd2' -> `/dev/sdc' from device.map.
grub-probe: info: adding `hd3' -> `/dev/sdd' from device.map.
grub-probe: info: Cannot stat `/dev/disk/by-id/usb-Seagate_Backup+_Hub_BK_NA8TT3NB-0:0', skipping.
grub-probe: info: Cannot stat `/dev/disk/by-id/usb-Seagate_Expansion_NA84KDR3-0:0', skipping.
grub-probe: info: /dev/sda1 is present.
grub-probe: info: Looking for /dev/sda1.
grub-probe: info: /dev/sda is a parent of /dev/sda1.
grub-probe: info: /dev/sda1 starts from 2048.
grub-probe: info: opening the device hd0.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 2048.
grub-probe: info: /dev/sda1 is present.
grub-probe: info: Looking for /dev/sda1.
grub-probe: info: /dev/sda is a parent of /dev/sda1.
grub-probe: info: /dev/sda1 starts from 2048.
grub-probe: info: opening the device hd0.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 2048.
grub-probe: info: /dev/sda1 is present.
grub-probe: info: Looking for /dev/sda1.
grub-probe: info: /dev/sda is a parent of /dev/sda1.
grub-probe: info: /dev/sda1 starts from 2048.
grub-probe: info: opening the device hd0.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Scanning for DISKFILTER devices on disk hd0.
grub-probe: info: Scanning for mdraid1x devices on disk hd0.
grub-probe: info: Scanning for mdraid09 devices on disk hd0.
grub-probe: info: Scanning for mdraid09_be devices on disk hd0.
grub-probe: info: Scanning for dmraid_nv devices on disk hd0.
grub-probe: info: Scanning for ldm devices on disk hd0.
grub-probe: info: scanning hd0 for LDM.
grub-probe: info: no LDM signature found.
grub-probe: info: Scanning for lvm devices on disk hd0.
grub-probe: info: no LVM signature found.
grub-probe: info: Partition 0 starts from 2048.
grub-probe: info: opening hd0,msdos1.
grub-probe: info: drive = 0.
grub-probe: info: the size of hd0 is 234441648.
grub-probe: error: not a directory.
```

---

### Post by slickymaster on 2018-09-28
*Thread moved to **Server Platforms**.*

---

