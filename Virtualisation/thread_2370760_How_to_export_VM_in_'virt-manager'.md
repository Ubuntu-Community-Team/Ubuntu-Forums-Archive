---
title: "How to export VM in 'virt-manager'?"
date: 2017-09-06
forum: Virtualisation
---

### Post by accounts0 on 2017-09-06
I had been using Virtualbox in which I got used to being able to periodically export an .ovh file that I could import later, like a backup separate from snapshots. Now I've converted that to run in KVM & I don't see any way to export/backup my VM in virt-manager. How can I export it similarly as I had been doing in Virtualbox?

---

### Post by TheFu on 2017-09-07
**qemu-img** is the command you want.

---

