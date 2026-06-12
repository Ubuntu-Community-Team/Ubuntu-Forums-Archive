---
title: "[SOLVED] Can I install Vista 64x on Virtualbox Ubuntu 32bit ?"
date: 2008-12-08
forum: Virtualisation
---

### Post by Sunnynight on 2008-12-08
When I insert the CD, the loading screen appears, then a message says that "this CPU is not compatible with 64-bit mode."

My laptop is M1330, T5850.

Is this CPU not compatible with 64bit ? or doesn't virtualbox support 64 bit ?
Thanks.

---

### Post by reacocard on 2008-12-08
Virtualbox only supports 64bit guests on a 64bit host with hardware virtualization support. In other words, you'll need to be running 64-bit Ubuntu to make it work, assuming your CPU is compatible. (I assume its a core 2 duo? if so its compatible.)

---

### Post by Sunnynight on 2008-12-08
> **reacocard said:**
> Virtualbox only supports 64bit guests on a 64bit host with hardware virtualization support. In other words, you'll need to be running 64-bit Ubuntu to make it work, assuming your CPU is compatible. (I assume its a core 2 duo? if so its compatible.)

Yes, it's core 2 dou. 

How about VMWARE ? Does it run x64 guest on x32 bit ?
Thanks

---

### Post by bodhi.zazen on 2008-12-09
You need to run a 64 bit host to enable a 64 bit guest (even if you are running a 32 bit OS on a 64 bit processor).

---

### Post by Sunnynight on 2008-12-09
Thanks. The only way is to use x64 host. SOLVED.

---

