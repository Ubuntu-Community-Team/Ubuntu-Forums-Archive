---
title: "Any Quantal GeForce 560Ti users?"
date: 2012-07-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by t1497f35 on 2012-07-14
Hi,
The daily live ISOs and the alpha fail after choosing to boot the live CD, they seem to corrupt video card's memory and the boot process never finishes.

I switched to an earlier nvidia card (GeForce 7600) and everything worked fine.

Anyone else has such problems with recent nvidia cards? Has it been reported as a bug?

---

### Post by monino on 2012-09-10
> **t1497f35 said:**
> Hi,
The daily live ISOs and the alpha fail after choosing to boot the live CD, they seem to corrupt video card's memory and the boot process never finishes.

I switched to an earlier nvidia card (GeForce 7600) and everything worked fine.

Anyone else has such problems with recent nvidia cards? Has it been reported as a bug?

The same problem here! I tried alternate (after install crash), 32 & 64 bits and nothing...

---

### Post by theanswriz42 on 2012-09-10
Yeah, same here, though I have a GeForce 330M. The way I got around it was to use the alpha alternate ISO and then upgrade from there. You'll have a lot of dependencies to have to manually go through which takes a bit of time but it'll work afterward. 

I think the decision to ditch the alternate ISO was pretty well misguided but at least there's a workaround.

---

### Post by cariboo on 2012-09-10
> **monino said:**
> The same problem here! I tried alternate (after install crash), 32 & 64 bits and nothing...

This problem has been discussed so many times in this sub-forum, I'm surprised you didn't find a solution to your problem.

Use nomodeset when booting the Live CD, to get around the corruption problem. As far as there not being an Alternative Install iso, just use the mini/netinst iso, it functions the same way, except that it downloads and installs the latest packages from the repositories. One great advantage, is that you don't need to do any updates after the installation is finished, as you already have the latest and greatest. :)

---

### Post by monino on 2012-09-11
> **cariboo907 said:**
> This problem has been discussed so many times in this sub-forum, I'm surprised you didn't find a solution to your problem.

Use nomodeset when booting the Live CD, to get around the corruption problem. As far as there not being an Alternative Install iso, just use the mini/netinst iso, it functions the same way, except that it downloads and installs the latest packages from the repositories. One great advantage, is that you don't need to do any updates after the installation is finished, as you already have the latest and greatest. :)
Solved :D In the installation and first boot i used "nomodeset" on the kernel line. Then I activated the proprietary driver and everything OK. :lolflag:

---

