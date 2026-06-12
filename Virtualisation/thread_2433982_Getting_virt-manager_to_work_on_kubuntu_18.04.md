---
title: "Getting virt-manager to work on k|ubuntu 18.04"
date: 2019-12-28
forum: Virtualisation
---

### Post by tobiz on 2019-12-28
After many hours of trying to a get clean install virt-manager to run on my clean install kubuntu 18.04 (but guess it also applies to ubuntu 18.04) I found the fault is a syntax error in /etc/libvirt/qemu.conf line 412. It should be: group="kvm" and not: group=kvm.  Once changed (under sudo) and running libvirtd -d and virt-manager under sudo I could finally get to create vm's.

---

