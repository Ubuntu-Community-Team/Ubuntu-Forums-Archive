---
title: "Xenial on Intel NUC Skylake:  Which Kernel To Track?"
date: 2016-03-17
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2016-03-17
I've got Xenial on an Intel NUC i5 Skylake. These units are new with a number of issues reported on Linux, including display hangs and freezes, poor power management and poor hardware acceleration support, and bricking resuming from suspend. Intel has released a series of BIOS updates.

I experienced very frequent display hangs and freezes with the 4.4 kernel shipping in the Xenial dailies. I'm currently using the 4.5.0-997 drm-next-intel kernel from the mainline PPA, which is behaving, so far.

I'm unsure how the drm-intel kernels relate to the other mainline kernels.  What should I track to stay current with the latest Skylake patches?

---

