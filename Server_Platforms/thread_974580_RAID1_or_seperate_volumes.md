---
title: "RAID1 or seperate volumes?"
date: 2008-11-07
forum: Server Platforms
---

### Post by CrucifiedEgo on 2008-11-07
So, I've been going back and forth on my home fileserver.  it currently is using software raid on the two 500GB SATA disks.  I'm thinking it's smarter to separate the volumes, and just rsync every 24 hours.  That way, I'm protected from both a disk failure, and an "ohshit"(think sudo rm gone wrong).  Can anyone see a downside to this (outside of the possibility of losing 24 hrs of data?)

Edit: subject spelling fail.  Sorry.

---

### Post by PilotJLR on 2008-11-07
Provided you can accept downtime and up to 24 hours of data loss, then a nightly rsync is a good idea - precisely for the reason you mention. Too many people setup a RAID array and then falsely think they don't need backups!

If you really want to get fancy, then primary storage can be RAID 1, with a third disk being mounted only for rsync backups every 6 / 12 / 24 hours, etc.

---

### Post by bshadow on 2008-11-08
Hy there.

I am really really new in the world of linux, ubuntu server, etc. And when I say really new, I meant it. I know nothing.

I have a question relating RAID 1.

Can you install Ubuntu server with RAID 1 on a MB without RAID capability?

I ask you because I enabled RAID in bios, and after the ubuntu server installation it woun't boot. I disabled the RAID in bios and it boots just fine.

I've used the RAID software that comes with Ubuntu server.

Thank you

---

### Post by PilotJLR on 2008-11-08
Yes, you can. Hardware RAID on a card or motherboard is not needed.

mdadm will basically take volumes/partitions/etc and apply raid levels to them.
For example, disk partitions sda1 and sda2 can become md0, which is a multi-disk device using RAID 1, RAID 0, etc... your choice.

---

### Post by bshadow on 2008-11-08
OK, thank you very much.

---

