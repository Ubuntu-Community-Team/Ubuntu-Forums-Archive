---
title: "lvm2 vg limited to 2TB"
date: 2017-03-13
forum: Server Platforms
---

### Post by david-whitmarsh on 2017-03-13
I have installed an 8TB drive as a second hard disk on a server, and created a single physical partition on it, however when I attempt to create a lvm2 volume group using the entire partition, I end up with a volume group of only 2TB, this is on Ubuntu server 12.04 with kernel 3.2.0-124-generic so, as I understand it, should not be subject to a 2TB limit on a volume group. I have tried increasing the physical extent size, but still the VG Size comes out at 2TB

How can I create a single volume group using the entire 8TB?

Output of smartctl:

[FONT=courier new]smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-124-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     HGST HUH728080ALE600
Serial Number:    VLH1EXMY
LU WWN Device Id: 5 000cca 260cec024
Firmware Version: A4GNT907
User Capacity:    8,001,563,222,016 bytes [8.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Mon Mar 13 18:42:56 2017 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled[/FONT]



Output of vgdisplay:

  [FONT=courier new]--- Volume group ---
  VG Name               vgstorage
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  1
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                0
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               2.00 TiB
  PE Size               32.00 MiB
  Total PE              65535
  Alloc PE / Size       0 / 0   
  Free  PE / Size       65535 / 2.00 TiB
  VG UUID               QyNCCU-ykx9-vpdW-GQet-y3hI-HSNu-0nVdu5[/FONT]

---

### Post by darkod on 2017-03-13
If the 8TB hdd is /dev/sda, post the output of:
```
sudo parted /dev/sda print
```

If the disk is different, modify the command and post that output. I think you might have msdos table on the disk which allows max 2TB partition. You say the partition is on the whole disk but maybe it isn't.

---

### Post by david-whitmarsh on 2017-03-13
Many thanks, that was the clue I needed. Using parted to create the partition solved the problem.

---

### Post by darkod on 2017-03-13
Great. Please mark the thread sa solved. You can do that in Thread Tools above the first post.

---

