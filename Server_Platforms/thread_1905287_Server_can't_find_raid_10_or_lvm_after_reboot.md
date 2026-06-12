---
title: "Server can't find raid 10 or lvm after reboot"
date: 2012-01-06
forum: Server Platforms
---

### Post by twgray on 2012-01-06
I am running Ubuntu Server 9.04.  Installation is on a standard SATA drive.  I have a large data drive created from 4 500GB drives set up with soft raid 10 with mdadm.  On the raid device I have created an LVM of about 1.36TB.

Last week after a power outage, at which time my UPS decided to die as well, I had to restart the server.  Upon boot the system cannot find the raid device or the lvm.  vgdisplay yields: no volume groups found.  df -Th shows only the installation drive /dev/sda1 mounted.

So, apparently, some files got corrupted.  Is there any way to recover from this?  Help!!!

---

### Post by twgray on 2012-01-06
Solved the problem.  From a console I entered the following:

sudo mdadm --create /dev/md2 -v --assume-clean --level=raid5 \
--raid-devices=4 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

Turned out it was a Raid5, not Raid10.  mdadm told me this when I first entered the above command with --level=raid10.

---

