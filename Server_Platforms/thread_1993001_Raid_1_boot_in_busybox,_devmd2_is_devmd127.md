---
title: "Raid 1 boot in busybox, /dev/md2 is /dev/md127"
date: 2012-06-01
forum: Server Platforms
---

### Post by dibuntux on 2012-06-01
The system, configured with ubuntu 10.04 and two WD disk (500GB and 750 GB, of which only 500 used) with 3 identical partitions set as /md0, /md1 & /md2. It was running fine for a year, then one of the disks showed some errors. I run a fsck from Gparted and an array check from Disk Utility (palimpsest) from an Ubuntu Live USB 11.10.
When I reset the system it booted in initramfs complaining that mount /dev/disk/by-uuid/(serialofdisk) on /root failed:invalid argument ...target filesystem does'nt have /sbin/init

if I cat /proc/mdstat the arrays are ok (UU) on /md0, /md1 and /md2
if I mdadm --detail --scan it shows the /md0, /md1 and /md2 arrays
but
if I mdadm --examine --scan it shows  /md0, /md1 and /md127 !
In mdadm.conf  arrays are correctly stated /md0, /md1 and /md2 array

So the array cannot be assembled becouse of this name messing, just becouse I checked the array from a LiveCD.

Do not know what to do; i cannot update-initramfs from initiramfs or LiveCD. 

What can I do? TIA

---

