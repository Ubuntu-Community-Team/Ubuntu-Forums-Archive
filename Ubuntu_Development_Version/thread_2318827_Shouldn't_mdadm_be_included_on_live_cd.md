---
title: "Shouldn't mdadm be included on live cd?"
date: 2016-03-29
forum: Ubuntu Development Version
---

### Post by dankegel on 2016-03-29
A system with RAID started having a weird network problem -- some sort of misconfiguration -- and like a coward, I decided to use a live cd to transfer its important files to another machine before wiping it and starting over.

Like cannon fodder, I decided to try this with ubuntu 16.04 beta 2's live cd.  (I didn't test with other versions.)

I admit, I haven't used raid hardly at all.   I was somewhat disappointed that the live cd didn't automount the system's raid partitions.
It took me several minutes of googling to find the workaround:
   sudo apt-get update
   sudo apt-get install mdadm
   sudo mdadm --scan --assemble

Shouldn't mdadm be included in the live CD?  It might be nice.

---

### Post by grahammechanical on 2016-03-29
It is in the server edition

[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)

Which, to my mind, is logical.

---

