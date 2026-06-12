---
title: "serial ata raid (stripe) 801.0 gb linux device-mapper"
date: 2011-03-15
forum: Server Platforms
---

### Post by capitalfear on 2011-03-15
WHAT!? i am so freakin out, ubuntu server keeps trying to partition my raid...i have a 3tb raid and i was just re-formatting, wiped everything clean, whats going on?! 64 bit

---

### Post by disabledaccount on 2011-03-15
I suppose You're talking about installer, not server - right?
If so, then it should be sufficient to uncheck formatting, what is possible in manual partitioning mode.

edit: In manual partitioning mode you should see dmraid partition, and it has to contain valid filesystem.
besides: why dmraid? have you moved those drives from some fakeraid controller? /edit

---

### Post by capitalfear on 2011-03-17
no this is server edition, i eve put in ubuntu 10.04 the regular, formatted everything and still had the problem, resetup RAID0 and still had the problem

---

