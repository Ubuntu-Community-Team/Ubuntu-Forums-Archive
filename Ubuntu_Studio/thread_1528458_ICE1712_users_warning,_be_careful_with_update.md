---
title: "ICE1712 users: warning, be careful with update"
date: 2010-07-10
forum: Ubuntu Studio
---

### Post by bluesscream on 2010-07-10
after update 7/7/2010 containing kernels 2.6.32-24 my ICE1712 card (Hoontech dsp24)  no longer is supported by Ubuntu's preempt and generic kernels. lsmod doesn't show up ICE1712 modules although the device appears
in lspci.
It continues working on all rt-kernels and on selfcompiled 2.6.34 an .35 ones
I just verify this on my not updated 32 bit experimental partition and find out that ICE1712 already did not work on ubuntu's 2.6.32-23 kernels.

---

