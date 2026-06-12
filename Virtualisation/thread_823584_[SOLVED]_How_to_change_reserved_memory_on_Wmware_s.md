---
title: "[SOLVED] How to change reserved memory on Wmware server?"
date: 2008-06-09
forum: Virtualisation
---

### Post by alelinuxbsd on 2008-06-09
**How to change reserved memory on Wmware server?**

Every time I try a change appears an error and i can't change this global settings.

---

### Post by fjgaude on 2008-06-09
Well, after loading the VM you have to power it down, then using its Settings to change anything you wish.

---

### Post by alelinuxbsd on 2008-06-11
I have resolved this problem with two step.

sudo vmware

After for launch vmware are normal user i have modified the owner (from root to username) of:
/home/username/.vmware/preferences

---

