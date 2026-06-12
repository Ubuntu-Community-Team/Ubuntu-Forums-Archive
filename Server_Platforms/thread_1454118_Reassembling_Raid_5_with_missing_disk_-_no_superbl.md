---
title: "Reassembling Raid 5 with missing disk - no superblock?"
date: 2010-04-14
forum: Server Platforms
---

### Post by deadball on 2010-04-14
Hey guys.

I've got a problem here:

One of my raid disks (was a software raid5 with 4 drives) failured. I wanted to buy a new 1.5TB harddisk anyway so i i copied all the Raid data onto the new disk and disconnected the old ones.

But then the new Disc crashed right before i could mirror it with another 1.5TB disk.

So i need to reassemble my old Raid 5 now.

I connected the drives in the former order except the first one, because this was the failed disk.

The problem is, mdadm can't find the raid, no superblocks. Fdisk doesnt show mdraid superblocks, too.
But fdisk has never showed superblocks.

The thing is, this raid was crypted, but i crypted the /dev/md0, so this doesn't affect anything here, or?

some infos:
```

server:~# mdadm --misc -d /dev/sda
mdadm: option -d not valid in misc mode
server:~# mdadm --misc -t /dev/sda
mdadm: /dev/sda does not appear to be an md device
server:~# mdadm --misc -t /dev/sdb
mdadm: /dev/sdb does not appear to be an md device
server:~# mdadm --misc -t /dev/sdc
mdadm: /dev/sdc does not appear to be an md device

```
```

server:~# mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/dm-2: Device or resource busy
mdadm: cannot open device /dev/dm-1: Device or resource busy
mdadm: cannot open device /dev/dm-0: Device or resource busy
mdadm: cannot open device /dev/sdd2: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: no recogniseable superblock on /dev/sdc
mdadm: no recogniseable superblock on /dev/sdb
mdadm: no recogniseable superblock on /dev/sda
mdadm: No arrays found in config file or automatically

```
```

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc703d08e

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd49fed3e

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b9e3db0

Disk /dev/sdc doesn't contain a valid partition table

```

But fdisk always said there is no valid partition table and the raid was working.

Does anybody have an idea?

Thanks!!

---

### Post by deadball on 2010-04-15
No ideas? :)

---

### Post by Cracauer on 2010-04-15
My first guess is that you were on partitions (sda1 etc) and now specified disks (sda with no partition digit). Possible?

Do you have any kind of /proc/mdstat output from when the old array was running?

A hexdump of the beginning of the disk might show where the heck the md superblock actually is.

---

### Post by deadball on 2010-04-16
Hexdump is a nice idea. How does the block look like?

No, i did not create any partition.

And i think i dont have a output, but i will search in my old logfiles! thx

---

### Post by deadball on 2010-04-19
Recreating via mdadm --create raid-level=5 raid-devices=4 missing /dev/sda /dev/sdb /dev/sdc

did it :)

---

