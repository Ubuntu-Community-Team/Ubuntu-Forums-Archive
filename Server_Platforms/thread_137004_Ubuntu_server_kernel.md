---
title: "Ubuntu server kernel"
date: 2006-02-27
forum: Server Platforms
---

### Post by geertn on 2006-02-27
I'm wondering about the Ubuntu server kernel. Which kernel version will this be (2.6.15?), and, will this version be maintained longer then the current "stable" release cycles of the vanilla kernel?

---

### Post by krewemaynard on 2006-02-28
[QUOTE=geertn]I'm wondering about the Ubuntu server kernel. Which kernel version will this be (2.6.15?), and, will this version be maintained longer then the current "stable" release cycles of the vanilla kernel?[/QUOTE]

Don't know about future versions (gave up on keeping up with that once I left Gentoo ;) ), but I'm currently using linux-image-2.6.12-10-686-smp on a P4 2.8 with HyperThreading (thus the SMP kernel, which treats the HT as 2 CPUs). If you compile your own, I'm sure you could get a higher version, but I'm happy with the stock kernel.

---

