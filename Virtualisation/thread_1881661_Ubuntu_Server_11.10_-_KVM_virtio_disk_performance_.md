---
title: "Ubuntu Server 11.10 - KVM virtio disk performance terrible, compared to 10.04"
date: 2011-11-15
forum: Virtualisation
---

### Post by ziggo0 on 2011-11-15
My home server was running Ubuntu Server 10.04.3 LTS for the longest  time, till I needed some virtual machines. KVM works great, it's fast,  good disk performance (160mb/s native, 120 to 140mb/s in the VM) - only  problem is saving/restoring of guests was bugged, kernel  upgrading/backporting didn't solve it. 

I tried to give Ubuntu Server 11.10 a go, and saving/restoring works  GREAT, much faster on saving and the restore feature actually  works....EXCEPT, I am getting absolutely horrible disk performance. 20  to 40, sometimes 50mb/s in guest, where it used to be nearly 3 times  that on older versions of kvm/ubuntu. I've tried kernel 3.1 & 3.2 RC  with no changes in performance. 

Am I missing something?

---

