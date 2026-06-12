---
title: "Fsck check of raid array member"
date: 2011-09-29
forum: Server Platforms
---

### Post by 6tangos on 2011-09-29
Hi,

I have a disk that keeps dropping out of Raid-1 array (mdadm - Ubuntu 10.04). Is it possible to run fsck on the disk in a separate machine? We need to be clear that the errors are with the disk and not the host machine (had some hardware issues in the past).

When running fsck with the disk on a separate machine I get an error along the lines of: "can't check disk, raid array member type not supported". Even when specifying type as ext3.

Any options?

Cheers,

Tom

---

### Post by lykwydchykyn on 2011-09-29
fsck is for checking the filesystem; if you have only one RAID member, you don't really have the actual filesystem on that disk, as I understand it.

Probably what you want is "badblocks", which will test the physical disk for bad sectors.

---

### Post by 6tangos on 2011-09-29
lykwydchykyn - thanks.

I thought it might be something like that, just had hope given that I can mount the drive on the separate machine using `mount -t ext3`.

I've got badblocks running currently and we'll just have to use that to assess whether it's the drive or something else.

---

### Post by lykwydchykyn on 2011-09-29
You can also check out smartmontools to view the SMART data stored on the drive.

---

### Post by 6tangos on 2011-09-30
Thanks again lykwydchykyn. 

The disk was dropping in/out of the bios on the original machine, but when it was visible smartmontool tests were inconclusive - it was marked as healthy! This was one of the reasons why I wanted to check on a different system.

Results from badblocks on separate machine showing a host of errors, the disk is being returned to manufacturer.

---

