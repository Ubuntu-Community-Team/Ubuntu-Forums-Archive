---
title: "High Virtualbox CPU usage with idle 64-bit lucid guest"
date: 2012-03-06
forum: Virtualisation
---

### Post by brickZA on 2012-03-06
Hi,

I'm running a 64-bit Ubuntu 10.04 (Lucid) server guest on a 64-bit natty (11.04) desktop host. Host machine is a fairly beefy laptop (dual-core i7, 8GB RAM). I find that when the Lucid VM is idle, the Virtualbox process takes about 25% CPU, as compared to about 5% for an idling 32-bit Ubuntu Jaunty (9.04) desktop idling in the GUI.

I have tried upgrading to the newest virtualbox 4.1 (using deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib non-free), and I also tried installing the linux-virtual kernel image in the guest, as well installing the pacakged virtualbox guest additions (except for the X11 package) in the guest. Nothing seems to have improved matters.

I am using VT-x/AMD-V and Nested Paging and also unticked "Enable IO APIC"

Seeing that the Jaunty guest uses so much less CPU, there must presumably be something I can do to the Lucid guest to improve matters. But what?

Thanks
Neilen

---

