---
title: "Raid 6"
date: 2009-01-05
forum: Server Platforms
---

### Post by Gyppie on 2009-01-05
Hi!

I have benn using ubuntu server with 4 drives in raid 5 (software raid) for about a year now. Resantly 2 drives became faulty at the same time, so I lost all my data. So I will replaqce all my drives.

However, should I stick to raid 5, or take the next step and go for raid 6? Does anyone have any experience with software raid 6 with mdadm?

Sorry for my bad english

Gyppie

---

### Post by Cracauer on 2009-01-05
No more Maxtor drives, eh? :)

MD's raid6 works fine for me.

But keep in mind you need some kind of backup anyway. You can have your PSU kill all drives, or you fatfinger something in the commandline and wipe your drives. Things happen.

Myself, I have partitioned my drives and the main area is a raid5. Then there are more important things that run on raid6. Swap is on two raid1 partitions.

In general you don't want more than one (set of) partitions in raid5, since you need to re-sync them after drive failures. You cannot sync more than one at a time, so while your first raid5 is synching the other raid5s run an extremely high risk of failure. So I have *one* raid5 and the important stuff lives on raid6. Plus a system of backups.

---

### Post by insane_alien on 2009-01-05
remember to try and get drives from different batches possibly even different manufacturers to ensure a production error can't take them all out.

---

