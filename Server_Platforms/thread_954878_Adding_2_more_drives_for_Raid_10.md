---
title: "Adding 2 more drives for Raid 10"
date: 2008-10-21
forum: Server Platforms
---

### Post by go_beep_yourself on 2008-10-21
I have 2 320gb sata2 Seagate drives in raid1 with mdadm in Ubuntu. I want raid10 with 4 drives. Should I buy the same size and model hard drives or go with bigger hard drives if they give me a better price per gigabyte? Does it work better to have all drives the same?

---

### Post by fjgaude on 2008-10-21
Software raid, mdadm, will use and create the array using the smallest of the drive set.

If you are not adding four big drives then two more of the same size as the old ones might be the high ticket.

Study the mdadm man pages to get more ideas of what is possible.

Here's more:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
 /usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

Let us know how you are doing.

---

### Post by nhbubba on 2008-11-07
My $0.02: I would buy larger drives. Then I would partition them into (at least) two partitions each, one being ~320GB in size to match the existing drives. You can then RAID10 the old drives and these partitions on the larger drives. Then you could build another RAID1 set out of the remainder of the new drives and use that space for other purposes.

That's what I would do (and have done) anyway..

---

