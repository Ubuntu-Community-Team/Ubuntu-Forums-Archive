---
title: "Ubuntu Server 8.04 MD Raid 1 problem"
date: 2009-03-25
forum: Server Platforms
---

### Post by Throwback on 2009-03-25
I am running a home server on Ubuntu 8.04 LTS Server on a Xen kernel with 5 hard disks.

I have a single Ide drive containing the root and swap partition (basically the system drive) on the motherboard's on board hard disk controller.

I also have a pci sata raid controller with 4 disks attached to it in two md raid 1s. Recently I suffered what appeared to be failure of one of the drives in the larger array (1TB). On closer inspection with fsck the drives both appear to be fine. However the raid array has managed to fall apart and I now have two perfectly readable/writeable reiserfs partitions. In fact ubuntu appears to have automatically mounted one of the partitions in the array onto the old mount point so the data is still readable/writeable to the system, but no longer as a mirrored array. Moreover I am not able to reassemble the array as I am informed there is no RAID superblock to read.

So I guess my first question is- where do I start looking to figure out where it all went wrong? Can anyone point me in the direction of an appropriate log that would contain the error messages the kernel spat out as the array failed? I have almost completed backing up the data on the array onto a third, external drive (rsync- taken 5 days for the 700GB of data...) so will not be taking any action until i have the backup secured. I would like to avoid recreating a blank array and copying the data back. I am aware I can create the array again using the old partitions and the data may be preserved but I am not sure of it. So firstly I am looking for help in doing the detective work and secondly to see if there is any shortcut rather than just wiping both disks in the array and starting from scratch as that could take some time to copy the data back.

Oh, and there is one other array in the machine (also raid1) which is currently unaffected and functioning normally.

Sorry for the long vague rambling post but its quite a problem to explain!

---

