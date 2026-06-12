---
title: "flashcache"
date: 2011-03-28
forum: Server Platforms
---

### Post by graylion on 2011-03-28
hi guys

had anybody ever tried flashcache [https://github.com/facebook/flashcache](https://github.com/facebook/flashcache) under ubuntu? My idea is to increase the throughput of a small server especially for database operations by using an SSD as cache.

---

### Post by BkkBonanza on 2011-03-28
Using an SSD is a good idea. 

I don't see what you'll gain by using flashcache. Linux already has file caching built in and delayed writes. I just had a qick look, so maybe they've improved on the linux kernel. It appears you need the kernel source to build it so I guess we can assume they are enhancing it.

---

### Post by graylion on 2011-03-29
Well, te point is to use the SSD as cache for a regular spinning disk. How is that supported in regular Ubuntu?

---

### Post by BkkBonanza on 2011-03-29
How big of a database are you expecting to have? Unless you have a huge database you would cache in RAM with database on SSD.

---

