---
title: "EXT4-fs (dm-0): bad geometry: block count 11987968 exceeds size of device (10939392"
date: 2020-04-15
forum: Server Platforms
---

### Post by mmiyamoto on 2020-04-15
[COLOR=#22231F][FONT=&amp]Hello,
does anyone have any idea, after restarting the server (vmware esxi), the ubuntu virtual server can no longer restart it stops in initramfs, I tried to start with a live version, however when I try to mount the LVM ext4 filesystem, the volume is activated, but ext4-fs bad geometry fails[2864.598363] EXT4-fs (dm-0): bad geometry: block count 11987968 exceeds size of device (10939392 blocks)root @ kali: ~ # mount / dev / mapper / MIXsrv1 - vg-root / mnt /mount: / mnt: wrong fs type, bad option, bad superblock on / dev / mapper / MIXsrv1 - vg-root, missing codepage or helper program, or other error.

[/FONT][/COLOR]Disk /dev/sda - 53 GB / 50 GiB - VMware Virtual disk
 Disk /dev/mapper/MIXsrv1--vg-root - 44 GB / 41 GiB - VMware Virtual disk
 Disk /dev/mapper/MIXsrv1--vg-swap_1 - 8585 MB / 8188 MiB - VMware Virtual disk
 Disk /dev/sr0 - 2936 MB / 2800 MiB (RO) - VMware Virtual IDE CDROM Drive
 Disk /dev/dm-0 - 44 GB / 41 GiB - VMware Virtual disk
 Disk /dev/dm-1 - 8585 MB / 8188 MiB - VMware Virtual disk

Disk /dev/sda: 50 GiB, 53687091200 bytes, 104857600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000d20ee


Device     Boot  Start       End   Sectors  Size Id Type
/dev/sda1  *      2048    499711    497664  243M 83 Linux
/dev/sda2       501758 104855551 104353794 49.8G  5 Extended
/dev/sda5       501760 104855551 104353792 49.8G 8e Linux LVM

---

