---
title: "UEC in two machine"
date: 2011-03-23
forum: Ubuntu Cloud and Juju
---

### Post by cloud25 on 2011-03-23
hi all,
 i had done private cloud setup on single machine by using VMware player.now i am decide to install CC on separate machine as guset throgh vm and also NC on separate machine as guest ..is it possible through Vmware player ???

---

### Post by kim0 on 2011-03-24
I think NC cannot be run under vmware, since it needs a VT enabled CPU! But I think you mention you already got it running (maybe you switched your hypervisor to qemu?)

Anyway, if you got it working on one machine, then yes I would think it should be possible to separate them on two different machines

---

