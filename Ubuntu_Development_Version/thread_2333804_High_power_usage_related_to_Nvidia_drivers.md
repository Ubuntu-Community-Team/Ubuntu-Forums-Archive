---
title: "High power usage related to Nvidia drivers"
date: 2016-08-13
forum: Ubuntu Development Version
---

### Post by fthx on 2016-08-13
Hello,

Using Yakkety Gnome, I get a high power usage. Roughly twice as Xenial's.
I tried gdm, lightdm, kernel 4.4 or new 4.6 (in proposed atm) but the bug is still here.

I ran top and powertop, and I suspect gnome-shell and/or Xorg but nothing's clear.

I use Intel (Skylake) gpu selected with Nvidia prime.
I suspect the upgrade Nvidia 361 -> 367 as I noticed when I was using Xenial, the v 367 from graphics drivers ppa gave me high battery usage too.

Anyone ? :-)

---

### Post by fthx on 2016-08-13
Ok, I downgraded to 361 and power usage is back to a low value. I'll report that on launchpad.

---

### Post by ventrical on 2016-08-13
367 will break .. usually bounce back to greeter in unity8.

Regards..

---

### Post by fthx on 2016-08-29
The same behaviour happens with Nvidia 370 from graphics drivers ppa.
So, I switched back to nouveau (thus using Intel) and power usage is low as before (twice lower...). I mainly use Nvidia with Windows 7 pro apps and I need some battery time for work.

It implies that high power usage is undoubtly Nvidia-related. I read some posts in Nvidia Linux forums that indicate it could be a missed turn off of Nvidia GPU with Nvidia settings (prime).

---

### Post by fthx on 2016-08-31
OOOOKKKK, in today's update :

**ubuntu-drivers-common (1:0.4.21) yakkety; urgency=medium**

**  * gpu-manager.c:**
**    - Make sure to load and unload the new nvidia-drm module.**
**      This fixes a problem that prevents the dGPU from being powered off**
[B]      in hybrid systems with recent nvidia drivers.

[/B]everything is back to normal power usage with proprietary Nvidia drivers 367.35 (and almost certainly 370).

---

### Post by fthx on 2016-10-10
I reached this bug again today, with nvidia 367.57 from proposed repository ATM.
I downgraded it to 367.44 from main repository and everything is back to normal.

---

