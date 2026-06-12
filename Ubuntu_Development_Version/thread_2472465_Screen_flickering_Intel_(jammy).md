---
title: "Screen flickering Intel (jammy)"
date: 2022-02-28
forum: Ubuntu Development Version
---

### Post by MyMurry on 2022-02-28
Hello,

with jammy I have sometimes a few seconds of screen flickering. I'm not able reproduce when.

With dmesg i found: 

i915 0000:00:02.0: [drm] *ERROR* CPU pipe A FIFO underrun

I tried the hints I found on the internet:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=4"
or
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=igfx_off"

But they doesn't work.

Any Hints?

---

