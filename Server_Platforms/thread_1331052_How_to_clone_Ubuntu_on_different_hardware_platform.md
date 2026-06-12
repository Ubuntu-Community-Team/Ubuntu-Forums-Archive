---
title: "How to clone Ubuntu on different hardware platforms"
date: 2009-11-18
forum: Server Platforms
---

### Post by deepakdeshp on 2009-11-18
Hi,

I want to make an image of my server on different hardware platforms, both machines having 64 bit AMD processors and different mother boards. I already have a running Ubuntu server on my destination machine .

The approach I was thinking was
[LIST=1]
[*]Retain the hardware driver, Kernel files etc.
[*]Copy all the other files except the hardware specific files from source to destination server. Use either tar or Bacula for this.
[/LIST]
This way I dont have to install all the applications and do the configurations.

Please suggest

---

### Post by Cheesemill on 2009-11-19
You can just clone the entire disk and boot it in the new server.
The linux kernel probes for new devices and loads the relevant drivers on every boot, so won't complain about the change of hardware (unlike Windows which is very unlikely to boot at all).

---

### Post by deepakdeshp on 2009-11-20
Thank you Cheesemill. I will try it out.

Regards,
Deepak

---

