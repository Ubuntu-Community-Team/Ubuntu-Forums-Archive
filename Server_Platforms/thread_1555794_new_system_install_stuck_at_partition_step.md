---
title: "new system install stuck at partition step"
date: 2010-08-18
forum: Server Platforms
---

### Post by morisot on 2010-08-18
I am trying to install 10.04 server, amd64 iso, on a brand new server with hardware SATA RAID preconfigured as RAID1.

The RAID controller is Intel, for a Xeon.  My conclusion is that I should not be installing software RAID, or fakeraid, but actual hardware RAID.  There is no setup guide for hardware RAID.  Also, I saw on one thread that I should not attempt a logical volume manager.

From what I can glean from online documentation I should be able to create three primary partitions, one for boot, one for swap, and one for root.  I select ext4 for boot and root.  I select bootable=on for the boot drive.  There are six combinations for this as far as order goes, and none of them work.

I am proficient at linux from a software developer perspective, but this system administration task has me baffled.

I can <go back> and then start a shell and look at /var/logs/syslogs and /var/logs/partman but I can't figure out what those logs are trying to tell me.

It seems to get farther if I use ext2 but then says something about a mount point and returns me to the partman setup.

---

