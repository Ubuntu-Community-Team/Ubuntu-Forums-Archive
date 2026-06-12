---
title: "No hdmi in Mantic with Nvidia/eGPU"
date: 2023-09-21
forum: Ubuntu Development Version
---

### Post by fthx on 2023-09-21
Hi,

I'm quite annoyed by this one: I get hdmi working only through Nvidia-only mode.
I do use a Legion laptop, Nvidia 3070.

My hdmi monitors are not detected using Intel (on-demand mode).
In fact, whole Nvidia gpu is not detected in this case (I cannot launch an app using dGPU in GNOME + no Nvidia gpu in system details in control center).
Same problem at work using an usb-c dock (then 2 monitors hdmi+dp).
I tested the 6.6 kernel too (from unstable ppa) but same issue.
Was ok running previous 6.3 kernel.

My guess is that ports are driven through Nvidia gpu BUT again this worked using 6.3.

Well: help!

---

