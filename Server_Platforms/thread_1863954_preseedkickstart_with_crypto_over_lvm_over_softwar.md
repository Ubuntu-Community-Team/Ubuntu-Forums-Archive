---
title: "preseed/kickstart with crypto over lvm over software raid"
date: 2011-10-18
forum: Server Platforms
---

### Post by mileswilson on 2011-10-18
This seems to be one of the least documented peices of ubuntu/linux I've come across yet :)


When setting up my 10.04LTS servers, I wish to achieve (and can, with the "gui" install):

Two 500GB disks, with two partitions, and each partition raided in RAID1.

First partition gets formatted, and called boot.

Second partition, gets LVM'd, and multiple volumes set up for / and swap

Both these LV's are then encrypted with LUKS. Resulting in full disk encryption.


Is it possible to do this preseeding? I've tried the following:

Using a script to do the raiding before trying to get partman-auto-crypto to run, with /dev/md0 as it's base disk. 

Seeing if I could manually create the RAID post install, with a script - this I think should be possible, but seemed an extremely convoluted way to go about it.


I can't be the only one wanting to use Crypto over LVM over RAID, or am I missing something really obvious?

Thanks

Miles

---

