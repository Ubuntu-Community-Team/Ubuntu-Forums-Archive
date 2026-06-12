---
title: "Ubuntu Login Loop and Screen Freeze"
date: 2017-09-14
forum: Ubuntu Development Version
---

### Post by lammert-nijhof on 2017-09-14
I installed 17.10 in June or so and update it each day. I still have the original login screen with the choices between "Gnome Wayland" and "Gnome Xorg", "Ubuntu Wayland" and "Ubuntu Xorg" or "Unity". I use Ubuntu 17.10 in Virtualbox 5.1.26. If I enable 3D acceleration for the guest "Ubuntu Wayland", Ubuntu gets in a login loop. Wayland only works, if I disable 3D acceleration. Not really unexpected I assume.
The "Ubuntu Xorg" version works with 3D acceleration most of the time and the Nightly Firefox version is remarkably efficient with respect to CPU usage and the host GPU is nicely occupied. Only when Firefox or Nightly Firefox are full-screen+ with respect to the VM screen, "Ubuntu Xorg" freezes and only a brute power-off will solve the problem. Most of the time it occurs, if the VM goes from full screen mode to windowed mode. Xubuntu and Ubuntu Mate (used to write this post), which I installed much later, do not have these problems.

 My daily driver(s) for e.g the financial stuff or my jukebox are  virtual machines and I use exactly the same VMs on desktop and laptop. I like that those problems are solved, so I try to determine, whether it is effective to raise bug-reports for these problems. So the questions are:
- Does anybody else has these problems and are both problems valid problems?
- Where should I report these problems with Mozilla, Ubuntu or with Oracle? Probably not Mozilla, because it occurs with both Firefox release 50 and Nightly Firefox.

---

### Post by ventrical on 2017-09-14
hi lammert,

This is the right place.I don't use virtual boxes .. just hard installs.. but likely it may be a problem with virtual machine .

Pehaps someone will see this that does use VMs.

Regards..

---

### Post by mauro-rossi on 2017-10-03
Hi ventrical,

the problem happens with all accelerated drivers and not only with virtual boxes 
and it is VERY annoying to upgrade a few days from release
and be stuck in a dummy login loop.

Could you please acknowledge that the problem is REAL and how to resolve?

Ubuntu is loosing points at each change perfomed because there is apparent lack of testing
Mauro Rossi

---

### Post by mc4man on 2017-10-03
> **mauro-rossi said:**
> 

the problem happens with all accelerated drivers and not only with virtual boxes 
and it is VERY annoying to upgrade a few days from release


Try with a fresh install of current image, if issues then you could file a bug(s), otherwise if using something from "June or so" your issues are somewhat irrelevant

---

