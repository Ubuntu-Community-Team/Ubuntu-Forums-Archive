---
title: "Virtual box ubuntu 64 bit on Windows xp 32 bit Bridged adapter not showing connection"
date: 2013-09-03
forum: Virtualisation
---

### Post by gajukorse-hegde80 on 2013-09-03
Hi i am using virtualbox 4.2.16 and installed ubuntu 13.04 64 bit but not getting dlink for bridged adapter . it is not showing any connection
please help me to solve this issue

---

### Post by TheFu on 2013-09-03
Virtual machines only see "virtual hardware", not the real stuff.  The virtual hardware that you want to select for networking should be a "virtio" driver.  Linux distros know about that device and have for 3+ yrs.

When you say "dlink" what, exactly, do you mean? 
Are there multiple NICs inside the physical machine? 
Are all of them physically connected to an ethernet network?
Is it possible that you un-checked the "cable connect" checkbox for the adapter?

---

