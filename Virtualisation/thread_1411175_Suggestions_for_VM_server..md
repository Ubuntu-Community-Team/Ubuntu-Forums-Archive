---
title: "Suggestions for VM server."
date: 2010-02-19
forum: Virtualisation
---

### Post by PinkFloyd102489 on 2010-02-19
I installed Ubuntu Server with virtual machine software option last night. At the moment, Im having a hard time figuring out what would be the most effective and easy setup.

Ive heard people mention HyperVM, Xen, KVM, QEMU, and Virtualbox. Right now, I have Vbox running just to demo VMs for some people. However, I would like to get an actual "VM server" running, possibly with a web management interface.

Ideas?

---

### Post by stlsaint on 2010-02-19
if your system is capable i would suggest going with kvm.

---

### Post by PinkFloyd102489 on 2010-02-19
> **stlsaint said:**
> if your system is capable i would suggest going with kvm.

Phenom x4 9650 2.3Ghz
Corsair 4GB 800mhz dual channel
500GB SATA hdd

---

### Post by pirateghost on 2010-02-20
with those specs i would go with a fullblown XEN or esxi.  they are both free and are purely hypervisors with low overhead

---

### Post by PinkFloyd102489 on 2010-02-20
> **pirateghost said:**
> with those specs i would go with a fullblown XEN or esxi.  they are both free and are purely hypervisors with low overhead

Im afraid I may run into the same problem with those that I did with JeOS. My onboard Realtek ethernet wasnt recognized by a bare minimum install. I had to install regular server with vm option in order to get drivers for my ethernet.

I can give it a try, thanks.

---

### Post by pirateghost on 2010-02-20
> **PinkFloyd102489 said:**
> Im afraid I may run into the same problem with those that I did with JeOS. My onboard Realtek ethernet wasnt recognized by a bare minimum install. I had to install regular server with vm option in order to get drivers for my ethernet.

I can give it a try, thanks.


yeah, the realtek will prove to be a problem with ESXi... spend 20-30 bucks for a decent intel pro nic.

---

### Post by chakoshi on 2010-02-21
I suggest kvm, dont have any experience with xen, but I've used several vm's on some kvm and esxi virtual machine hosts and kvm performs very well. the only problem is that the gui (virt-manager) really sucks! it frequently hangs and many features of it are not working (at least on ubuntu systems)

---

### Post by PinkFloyd102489 on 2010-02-21
> **chakoshi said:**
> I suggest kvm, dont have any experience with xen, but I've used several vm's on some kvm and esxi virtual machine hosts and kvm performs very well. the only problem is that the gui (virt-manager) really sucks! it frequently hangs and many features of it are not working (at least on ubuntu systems)

I used virt-manager for about 20 seconds before I started disliking it. Vbox is so much better, imo.


Does Xen have a web interface?

---

### Post by chakoshi on 2010-02-22
> **PinkFloyd102489 said:**
> I used virt-manager for about 20 seconds before I started disliking it. Vbox is so much better, imo.


they are not good choice for comparison, they are different in nature. virtualbox is a desktop virtualization application. but the virt-manager is a simple GUI to the libvirt packages (that provide some tools for managing and creating VMs) for xen/qemu/kvm server virtualization applications.

---

