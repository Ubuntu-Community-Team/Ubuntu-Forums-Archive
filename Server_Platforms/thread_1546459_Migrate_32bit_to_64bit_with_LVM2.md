---
title: "Migrate 32bit to 64bit with LVM2?"
date: 2010-08-05
forum: Server Platforms
---

### Post by gersoid on 2010-08-05
My home server has 2 SATA drives, drive 1(750GB) and drive 2 (1TB). 
Drive 1 has a bootable OS partition (20GB), a swap partition (2GB). The rest of disk 1 plus all of drive 2 is arranged into a single striped logical volume using LVM2, onto which /home is installed.
Under 9.10 32bit this worked fine, so webmin reported a /home of ~1.6TB

Ran upgrade to 10.04 32bit from 9.10 32bit - all went horribly wrong, can't boot, can't see eth0. Booting off CD still sees the relevant partitions, but because its not immediately obvious what the root cause is, and I have limited time over the weekend, it's probably much easier to do a clean install into the OS partition of 10.04, and then restore the various config files for the server applications, rather than spend the time looking for fixes on the interwebs, with low chance of success.

All data has been backed up.

Question: Given that I'm clean installing, I may as well upgrade to 64bit. If so, is there anything related to 64 bit OS using an LVM2 volume created with 32 bit OS? I'm aware that I'll have to fiddle with the LVM2 volume anyway, and it may not work, I'm really just checking that I'm no worse off with a 64- rather than a 32-bit clean build, simply because its 3 hrs to pull the contents of /home off the backup, shoudl I have to do a complete rebuild.

---

