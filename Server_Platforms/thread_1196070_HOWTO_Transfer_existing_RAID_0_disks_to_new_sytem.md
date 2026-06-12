---
title: "HOWTO Transfer existing RAID 0 disks to new sytem?"
date: 2009-06-24
forum: Server Platforms
---

### Post by coolaj86 on 2009-06-24
Assuming:
[LIST]
[*]I'm running Ubuntu 8.10 on OldServer
[*]I have 3-disk stripped RAID 0 inside OldServer as /mnt/data on /dev/md1
[*]I have a fresh install of Ubuntu 9.04 on NewServer
[/LIST]

I want to:
[LIST]
[*]Remove the 3 disks from OldServer
[*]Insert the 3 disks into NewServer
[*]Activate and mount the RAID Array on NewServer as /mnt/data on /dev/md0 (or whatever)
[/LIST]

How can I register the existing raid on the disks with the new system?

---

### Post by alastair on 2009-06-24
You want to look at "assembling" the old array on the new system i.e. using mdadm and "assemble" mode. Please read the mdadm man page before proceeding.

You might get away with just a search for raid partitions (fd) to assemble i.e.

mdadm --assemble /dev/md1
or
mdadm --assemble /dev/md1 /dev/sda1 /dev/sdb1 .. or whatever

Check the man page, and if in doubt, ask on the linux-raid list perhaps.

---

### Post by coolaj86 on 2009-06-25
I started by trying a few things that didn't seem to have any positive effect, but since they were part of the process I'll list them:

```

sudo mdadm --assemble /dev/md1 /dev/sda5 /dev/sdb5 /dev/sdd5
sudo mdadm --assemble --scan /dev/md1 /dev/sda5 /dev/sdb5 /dev/sdd5
sudo cat /proc/mdstat

```

I'm pretty sure this is what actually worked the magic.
```

sudo mdadm --examine --scan /dev/sda5 /dev/sdb5 /dev/sdd5
ARRAY /dev/md1 level=raid0 num-devices=3 UUID=1f78be10:e0fa3727:dbefc0ff:bf34ee59
vim /etc/mdadm/mdadm.conf
# added this line towards the bottom
ARRAY /dev/md1 level=raid0 num-devices=3 UUID=1f78be10:e0fa3727:dbefc0ff:bf34ee59
sudo reboot

```

It also had the wrong type of array (RAID0 rather than RAID1) listed for my boot partition (odd since it booted with no problem) so I also made that minor correction while I was in there.

I think I understand the configuration now so feel free to PM me if you(future problem-havers) have any questions.

---

