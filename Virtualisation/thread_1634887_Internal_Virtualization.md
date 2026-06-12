---
title: "Internal Virtualization"
date: 2010-12-01
forum: Virtualisation
---

### Post by mark_smith111 on 2010-12-01
I am new to virtualization and I am working on putting an Internal Virtualization plan in place. I will greatly appreciate if you could help me understand, Under what circumstances is VMWare Virtualization and/or RHEV and/or Xen and/or Microsoft Hyper V is better over the rest.  Also, is it reasonable to assume, all that needed to be virtualized on VMware has already occured.  Thanks for your help

---

### Post by CharlesA on 2010-12-01
Xen and VMWare's ESXi are "bare metal" hypervisors, in that they run their own OS that is dedicated to serving as a host for virtual machines.

It all depends on what you want to do with your virtualization environment.

For example, I am running Lucid x64 with VirtualBox on my server (which is doing more then just acting as a VM host). It works well for what I want to do, but if I wanted a dedicated VM host, I'd use something like Xen, KVM, or ESIx.

Does that answer yer question?

---

