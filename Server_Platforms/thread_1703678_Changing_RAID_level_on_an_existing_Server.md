---
title: "Changing RAID level on an existing Server"
date: 2011-03-09
forum: Server Platforms
---

### Post by pktrivedi on 2011-03-09
Hi all,

We have been using Ubuntu Server at our department since several months now.
It hosts a website, e-mail and nfs(only intra).

It was set-up as RAID 0 with two 1TB Hard drives but I want to change it to RAID 1 for fault tolerance. Is it possible to change existing RAID level? If yes can someone point me to the proper place? 

I tried "mdadm" documentation and level set option is available but no explanation available that whether it is only while creating the array or it can change the level too.

---

### Post by rubylaser on 2011-03-09
You can't use mdadm's grow option to covert a raid0 to any other raid level.  If you want to set this up, you'll need to back up your data, and then re-create the array.

> Grow (or shrink) an array, or otherwise reshape it in some  way.
              Currently supported growth options including changing the active
              size of component devices and  changing  the  number  of  active
              devices  in RAID levels 1/4/5/6, changing the RAID level between
              1, 5, and 6, changing the chunk size and layout  for  RAID5  and
              RAID5, as well as adding or removing a write-intent bitmap.


Notice no mention of growing raid0.

---

