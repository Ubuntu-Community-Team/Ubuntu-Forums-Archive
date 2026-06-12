---
title: "Anyone have experience with FlexRAID?"
date: 2010-07-18
forum: Server Platforms
---

### Post by wesg on 2010-07-18
I've just set up LVM on my server, but after talking to a friend, I think I need to consider backups into the picture. I've read about FlexRAID only a little, and it sounds good for what my server does (media archive) but I'd like some more info before proceeding. 

Has anyone installed it on a TB+ server with multiple drives? Any suggestions or warnings?

---

### Post by Gralgrathor on 2011-04-21
> **wesg said:**
> Any suggestions or warnings?

My own advice to myself was: wait until v2.0 for Linux becomes a Final in stead of a Beta or Preview with expiry date.

But I'm afraid I could be waiting forever for that to happen, so I've gone on looking for other solutions. How about you?

---

### Post by rentarou on 2011-04-21
> **wesg said:**
> I think I need to consider backups into the picture. 

Keep in mind RAID is not a form of backup, it's a from of redundancy to ensure uptime. It protects (to certain degrees) against hardware failure, but is still very vulnerable to software (or user) failure.

---

### Post by RocKKer on 2011-04-21
Have you tried mdadm software RAID? Not sure of the differences between that and Flexraid, but I store my media using mdadm software RAID5 on 4X2TB WD Greenies, took a bit to figure out how to partition these "Advanced Format" drives correctly, but they work great!

---

### Post by parisv on 2011-07-28
> **RocKKer said:**
> Have you tried mdadm software RAID? Not sure of the differences between that and Flexraid, but I store my media using mdadm software RAID5 on 4X2TB WD Greenies, took a bit to figure out how to partition these "Advanced Format" drives correctly, but they work great!

I'm thinking about doing the same. What do you mean about Advance Format? Is there a different way then usual for setting up mdadm.

I'm just buying my kit now but in a virtual machine I did this:

sudo mdadm --verbose --create /dev/md0 --metadata 1.2 --level=5 --raid-devices=4 /dev/sd[bcde]1

Is that right?

---

### Post by a2j on 2011-07-28
wd green drives need to be formatted starting on 64th block and not the default 63rd. search advanced format ;)

---

### Post by parisv on 2011-07-28
ok will do. Thanks for that. Glad I came across your post!

---

### Post by parisv on 2011-07-28
just incase anyone needs this info on advanced format it's here:

[http://linuxconfig.org/linux-wd-ears-advanced-format]("http://linuxconfig.org/linux-wd-ears-advanced-format")

---

