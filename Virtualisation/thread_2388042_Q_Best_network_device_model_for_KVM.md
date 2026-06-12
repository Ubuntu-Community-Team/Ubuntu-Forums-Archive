---
title: "Q: Best network device model for KVM"
date: 2018-03-27
forum: Virtualisation
---

### Post by linuksguru on 2018-03-27
Hi !

What is the best network device model for KVM in terms of reliability - virtio, e1000 or RTL8139 ?
VM had to run as router for years in unattended mode.

Thanks in advance for any suggestion(s).

---

### Post by TheFu on 2018-03-27
They all work. I've been using virtio for 8+ yrs and have used PRO/1000 (e1000) on Windows for about a year, before finally switching over to virtio devices.  

On Windows, going to virtio for disks can make fixing boot disk issues more complicated if you don't have a habit of loading special drivers for disk controllers from the Recovery Mode boot options.  Usually takes me 15 minutes to figure it out before I finally remember to load virtio drivers.   

For almost all linux guests, using virtio is fully supported.

---

