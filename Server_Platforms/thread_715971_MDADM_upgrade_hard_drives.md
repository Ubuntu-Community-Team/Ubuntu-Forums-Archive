---
title: "MDADM upgrade hard drives"
date: 2008-03-05
forum: Server Platforms
---

### Post by ihavenoideax2 on 2008-03-05
Currently i have 2 Seagate 320gb drives in 2 mdadm RAID1 arrays. /dev/md0 is 270gb and /dev/md1 is 28gb in size. I need more hard drive space on this server and was planning on upgrading from these drives to the new ones and moving all the data over to the new arrays. I currently cannot try anything because i cant afford new hard drives but im asking for when i do/if i get them. Im not to advanced with linux partitioning and want to learn how to.

---

### Post by bigredradio on 2008-03-20
You might want to consider using LVM when you upgrade your drives. Then in the future if you want to add more space it is a simple task. Take a look at the many LVM how-tos on the web. You can mirror the disks using LVM (although it is a much different procedure than RAID with mdadm.)

---

