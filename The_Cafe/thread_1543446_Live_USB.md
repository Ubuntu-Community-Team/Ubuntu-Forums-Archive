---
title: "Live USB"
date: 2010-08-01
forum: The Cafe
---

### Post by ged25 on 2010-08-01
How good is it to use a USB flash drive as a Live USB? I read somewhere that flash drives are not meant to be used for stuff like that unlike a CD. Will using the flash drive for this purpose reduce the life of the flash drive ?

---

### Post by NightwishFan on 2010-08-01
The USB Creator program in Ubuntu is similar to a live CD and stores changes in virtual memory (and optionally a persistence file) so that writes to the disk are not nearly as often. It is quite fine to use the Live USB, no different than normal usage. I have had a USB drive work with this method for years now.

What you should avoid is *installing* a system on a USB drive the normal way, as it will constantly read/write. This is achievable with some skill and work to reduce disk writes, however I do not recommend it.

---

