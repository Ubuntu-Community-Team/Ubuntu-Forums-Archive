---
title: "Warning: KVM is not available (Trusty)"
date: 2014-08-27
forum: Virtualisation
---

### Post by kevpatts2 on 2014-08-27
Hey all,

I get this warning when creating a new VM inside virt-manager and VMs are running very slow:
Warning: KVM is not available. This may mean the KVM package is not installed, or the KVM kernel modules are not loaded. Your virtual machines may perform poorly.

I've checked using lsmod and the "kvm" kernel module is loaded, but the /dev/kvm device does not exist.

Installed into default ubuntu server install using:
sudo apt-get install virt-manager libvirt-bin bridge-utils qemu-kvm

Anyone else having the same problem?

---

### Post by TheFu on 2014-08-27
KVM runs on the hostOS, not inside a clientOS/guestOS.
Is that what you are attempting?

dpkg -l|grep kvm

---

