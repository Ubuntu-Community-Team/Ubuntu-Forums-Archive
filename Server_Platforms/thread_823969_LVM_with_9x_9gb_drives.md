---
title: "LVM with 9x 9gb drives"
date: 2008-06-09
forum: Server Platforms
---

### Post by quietas on 2008-06-09
I've got an older dual p3 system I'm planning to set up as a transparent proxy here at work. I've got an external case, an Adaptec 2940, and a pile of SCSI 9gb drives. Unfortunately I don't have a spare hardware RAID card handy.

Anyway I want to set these up in an LVM using 8.04 server, but as I am not familiar with LVM the install is not straight forward. Any recommendations or how-to's that I missed?

---

### Post by quelx on 2008-06-09
May I suggest a raid 5 array using **mdadm**?
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by windependence on 2008-06-10
Personally I would set up LVM as he wants to. I don't like software RAID.

You can set up all the drives in one big LVM group and then partition space as if it was one storage pool. Leave some space in case you need more room on one of the partitions and you can then allocate some of the free space to the partition where you need the space without rebooting on the fly. LVM is great.

-Tim

---

