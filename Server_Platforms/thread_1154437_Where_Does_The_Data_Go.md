---
title: "Where Does The Data Go?"
date: 2009-05-09
forum: Server Platforms
---

### Post by jimmm33 on 2009-05-09
I'm replacing my old Windows 2000 Server with 9.04. It needs to serve up one app, media and shared files for a few Linux clients and two Windows clients.

My question is where do I put the shared data? Should it be on a different partition than the OS? If not, do I create a /data directory at the root of hda1?

---

### Post by pbpersson on 2009-05-09
I would never put shared data in the root partition for the simple reason that if it fills up, you could crash your OS.

You can create as many partitions as you want.

On this machine I have two Sata drives for storage, I named the folders SATA2 and SATA3 and mounted them in my /home/phil/SharedData folder

---

### Post by jimmm33 on 2009-05-09
> **pbpersson said:**
> I would never put shared data in the root partition for the simple reason that if it fills up, you could crash your OS.

You can create as many partitions as you want.

On this machine I have two Sata drives for storage, I named the folders SATA2 and SATA3 and mounted them in my /home/phil/SharedData folder

Great! Thank You.

---

