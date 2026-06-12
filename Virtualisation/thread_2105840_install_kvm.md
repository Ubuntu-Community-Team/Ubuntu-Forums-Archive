---
title: "install kvm"
date: 2013-01-17
forum: Virtualisation
---

### Post by spanfish on 2013-01-17
Hello everyone,
I want to install kvm on my desktop PC to learn virtualization, my cpu is intel Core i3, and I found it support VT-x on intel's page, I also enabled virtualization in BIOS,
however, I cann't find vmx flag from /proc/cpuinfo. when I create new guest os in virt-manager, I got the message:
*No hypervisor options were found for this connection.*
*This usually means qemu or kvm is not installed on your machine.* 
 
I can modprobe kvm, but can not modprobe kvm-intel, it got operation not supported error.Does it mean that my cpu doesn't support kvm?

---

### Post by ibjsb4 on 2013-01-17
Why not just ask your processor :)

```
kvm-ok
```

Edit: Not that there is anything wrong with kvm, but most people in this forum go with VirtualBox.  Just wondering why you chose kvm.

---

