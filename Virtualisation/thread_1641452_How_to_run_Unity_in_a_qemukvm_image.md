---
title: "How to run Unity in a qemu/kvm image"
date: 2010-12-09
forum: Virtualisation
---

### Post by mindless1973 on 2010-12-09
Hi,

I would like to test 10.10 netbook remix in a kvm instance. However, up to now, I did not manage to get unity working. 

Originally I used the default VGA adapter of qemu/kvm (cirrus), but got an error message during the very first reboot, that there is no suitable driver available - and the desktop switched back to standard GNOME.

How can I use unity within qemu/kvm?

any hints welcome!

bye
me.

---

### Post by dcstar on 2010-12-11
> **mindless1973 said:**
> Hi,

I would like to test 10.10 netbook remix in a kvm instance. However, up to now, I did not manage to get unity working. 

Originally I used the default VGA adapter of qemu/kvm (cirrus), but got an error message during the very first reboot, that there is no suitable driver available - and the desktop switched back to standard GNOME.

How can I use unity within qemu/kvm?


The Unity desktop will only run in a full 3D graphics environment, no VM I know of provides that as yet.

---

