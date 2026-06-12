---
title: "Ghost in the RAID"
date: 2010-04-06
forum: Server Platforms
---

### Post by artokarp on 2010-04-06
My system is Ubuntu 9.04 running with RAID 1 assembled out of two disks: /dev/sda2 and /dev/sdb2

When i start my Ubuntu box, i get a "Raid Degraded message" and an error about how /dev/sdc disc was not found, which is not part of my RAID. However if i start my computer and check details of my raid with mdadm i see this:

```

/dev/md0:
        Version : 00.90
  Creation Time : Fri Feb  8 04:47:07 2008
     Raid Level : raid1
     Array Size : 975707648 (930.51 GiB 999.12 GB)
  Used Dev Size : 975707648 (930.51 GiB 999.12 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr  6 16:31:58 2010
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 57% complete

           UUID : b40e94e4:6191647d:ceda455f:8a201cce
         Events : 0.21455

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2

```

(RAID is rebuilding because my system crashed because of a power outage, but that should not be related to this.)

So there isnt an /dev/sdc disk in my RAID, except, of course, if i run install-grub which gives me:
```

Searching for GRUB installation directory ... found: /boot/grub
[COLOR="Red"]**error: array->nr_devs > array->total_devs (2)?!?**[/COLOR]
Installing GRUB to /dev/sda1 as (hd0,0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd

```

So there is a disk in my RAID, which is not in my RAID. WTF?

Now /dev/sdc does in deed exists in my system, but it is not a RAID disk.

So how do i remove a disk from RAID that does not exist i my RAID?

---

### Post by ian dobson on 2010-04-06
Hi,

Do you actually have a sdc? If not just manually edit /boot/grub/device.map so that it only includes the drives that you have.

Also what do you see when you to a fdisk -l

and maybe have a look at your mdadm.conf file in /etc/mdadm

Note when linux boots it uses an "inital ram disk" load all drivers required to get the / up and running. In this case there is a mdadm.conf in /etc/mdadm which is "hidden" in the ram disk. To recreate the ram disk use  update-initramfs -u

To have a look at the contents of the init rammdisk go to /tmp then enter:-

gunzip -c /boot/initrd.img-2.6.31-20-generic | cpio -id

where 2.6.31-20-generic is the kernel version.

Regards
Ian Dobson

---

