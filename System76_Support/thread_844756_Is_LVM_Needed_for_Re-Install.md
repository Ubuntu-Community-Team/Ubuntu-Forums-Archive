---
title: "Is LVM Needed for Re-Install?"
date: 2008-06-29
forum: System76 Support
---

### Post by DomIncollingo on 2008-06-29
I've got a Serval (serp3) with 4GB of memory and a 200 GB hard drive running 32-bit Gutsy (installed by System 76).  I'd like to do a fresh install of 64-bit Hardy.  Do I need to worry about LVM partitioning when I install Hardy on the Serval, or can I just use the default ubuntu partitioning?  I'm not planning to do a dual boot.  I just want 64-bit Hardy on the laptop - no other OS.  Does LVM buy me anything?

Thanks very much.

Dom

---

### Post by thomasaaron on 2008-06-29
No. I'd recommend *not* using LVM. It severely limits your ability to modify partition sizes later down the road.

---

