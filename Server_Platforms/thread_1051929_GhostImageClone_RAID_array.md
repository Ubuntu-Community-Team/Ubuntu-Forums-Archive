---
title: "Ghost/Image/Clone RAID array"
date: 2009-01-27
forum: Server Platforms
---

### Post by rigged 00 on 2009-01-27
Hi

Does any one know how or what app will work good to make a restorable image of a complete raid array. Most of the servers I want to do this makes use of Raid 5, Raid 0 and raid 1 (some software raid others Hardware raid).

Someone suggested using something Like Norton Ghost or G4L (ghost for Linux), but as far as I know they don't work with Raid - or am I just being stupid :P

Any good apps or methods to accomplish this (with hardware and Software Raid) will be awesome....THX

---

### Post by Vegan on 2009-01-27
On my Windows box I have Partition Magic (PM) which can see a Ext2/3 partition and can convert them. I used it to recover files from a server that stopped booting once.

The RAID is a tad more complicated as they depend on the machine's hardware.

I do not have Ghost so I am not sure if it likes Ext2/3 partitions like PM does.

---

### Post by rigged 00 on 2009-01-28
Thanks for the reply Vegan. I have used Norton Partition Magic before and it works quite well for if you want to access EXT2/3 and repartition them, but it lacks the drive imaging capabilities (my version is a bit old, but I will check the new versions) as what Norton Ghost has.

---

