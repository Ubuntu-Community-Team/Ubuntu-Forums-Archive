---
title: "SAS/Ultra320 controller support..."
date: 2008-07-06
forum: Server Platforms
---

### Post by leadhead on 2008-07-06
I want to get a PCIE controller with 4 scsi drives...probably raid5. I just wanted to know what brands are supported and if anyone is running a white box server with a slotted controller card, what they had and if it runs well. I am doing a clean install of 8.04 and this will be my first experience with Ubuntu Server.

I love my gutsy laptop!!!

---

### Post by cariboo on 2008-07-06
Nobody ever went wrong buying 3ware.

Jim

---

### Post by ixus_123 on 2008-07-06
lsi megaraid works well in ubuntu, RHES4/5 etc.

Not cheap but really good cards imo

---

### Post by windependence on 2008-07-07
Linux supports most SCSI cards well. You should probably stay away from adaptec since they haven't open sourced their drivers. Some of their cards work but not like the LSI stuff. You can get some Dell Perc stuff on eBay, most of it is LSI stuff.

-Tim

---

### Post by leadhead on 2008-07-07
Thanks a million,that is exactly what I wanted to know.

---

### Post by ixus_123 on 2008-07-07
just a note on the dell perc6 stuff, it's pretty new and I've had trouble with drivers when trying to clone disks with ghost.

Just a thought, should you ever need to.  Perc5 worked fine.  I guess being a linux forum I should be using something like dd ;)

---

### Post by windependence on 2008-07-07
Hehe, my cards are still Perc3's. :)

-Tim

---

### Post by leadhead on 2008-07-07
> **ixus_123 said:**
> just a note on the dell perc6 stuff, it's pretty new and I've had trouble with drivers when trying to clone disks with ghost.

Just a thought, should you ever need to.  Perc5 worked fine.  I guess being a linux forum I should be using something like dd ;)

Gotcha, I am looking at perc 5i cards on ebay for like 200 bucks. This should do everything we need.

---

### Post by windependence on 2008-07-07
Seems a bit pricey though. I picked up the Perc 3's brand new for $60 each.

-Tim

---

### Post by leadhead on 2008-07-07
> **windependence said:**
> Seems a bit pricey though. I picked up the Perc 3's brand new for $60 each.

-Tim


I may do that, but SAS + Battery backed write cache is nice. The server is running a database app that is loading down sata drives.

---

### Post by windependence on 2008-07-07
I'm not sure about SAS, but the 3's had battery backed write cache. Decent cards, even with their age.

-Tim

---

