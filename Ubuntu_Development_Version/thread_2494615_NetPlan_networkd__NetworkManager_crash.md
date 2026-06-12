---
title: "NetPlan networkd / NetworkManager crash"
date: 2024-01-22
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2024-01-22
I'll file it tomorrow and post the URL. It's been a long day.

I 'debian-update'd' from 22.04.3 to 24.04... it was on networkd as the renderer, and working fine on 22.04.3. On the update to the current 24.04 repo, somehow the netplan scripts have a problem, and even though the netplan yaml was point to netword, and NetworkManager was stopped, disabled & masked, it kept trying to start that NetworkManager service.

On netplan apply, it would throw errors saying it couldn't start NetworkManager so exited out with errors...

I ended up turning off networkd, and starting NetworkManager back up. Ugh.

---

### Post by MAFoElffen on 2024-01-22
The Bug Report: [https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2050097](https://bugs.launchpad.net/ubuntu/+source/netplan.io/+bug/2050097)

---

### Post by MAFoElffen on 2024-01-27
I made some progress. There is a problem somewhere in the scripts. The prolem seems to occur if you try to convert a Desktop Edition from NetworkManager to using networkd as the renderer. Somethig in the scripts creates an ambigious netplan yaml file that conflicts with the main file, and... The overrides for the renderer are not working.

---

### Post by #&amp;thj^% on 2024-01-27
Thanks for the share, I read the Bug-Report as well.
I don't think the person that replied to you was fully awake yet. ;)

---

