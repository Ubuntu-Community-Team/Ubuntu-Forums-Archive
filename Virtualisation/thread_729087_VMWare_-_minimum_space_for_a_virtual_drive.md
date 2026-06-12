---
title: "VMWare - minimum space for a virtual drive?"
date: 2008-03-19
forum: Virtualisation
---

### Post by CoffeeBreath on 2008-03-19
What is the smallest amount of space I should set aside for a virtual drive running XP?

as in 

"qemu-img create -f vmdk vmware/WindowsXPPro.vmdk ???"

---

### Post by dacorr on 2008-03-19
depends what your going to use it for, for windows XP i keep a min of at least 4GB or 8GB depending on design.

You could always create an expanding vmdk image (keep in mind these dont shrink)

Dacorr

---

