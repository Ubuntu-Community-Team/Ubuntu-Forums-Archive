---
title: "Ubuntu 20.04 server erratic wired connection behavior"
date: 2020-07-03
forum: Server Platforms
---

### Post by siegfred2 on 2020-07-03
Hi,

I am currently trying to setup Ubuntu 20.04 server in my Raspberry Pi4, However i get  a problem,

The network seems to go to sleep / suspend / powersave when left unattended or no connection transaction happening for a few minutes.

I.E.

- After connecting via SSH and leaving it alone for a few seconds, first few inputs would lag for a few seconds, as if waking up. but ssh is not dropped.

- TCP request hangs for a few seconds after minutes of inactivity.

This only happens after i set my static IP via netplan and then disabling cloud-init.

Any one familiar with this "sleeping" issue?

---

