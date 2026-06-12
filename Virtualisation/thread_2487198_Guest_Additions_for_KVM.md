---
title: "Guest Additions for KVM"
date: 2023-05-27
forum: Virtualisation
---

### Post by satimis on 2023-05-27
Hi all,

I haven't run KVM for some time.  Would SPICE guest additions be the guest additions for KVM, like the guest additions for VirtualBox ?

SPICE guest additions
[https://www.spice-space.org/download.html#guest](https://www.spice-space.org/download.html#guest)

Please advise.  Thanks

Regards

---

### Post by ajgreeny on 2023-05-27
I think you will find that all the "spice" requirements you need are installed when you install virt-manager, kvm and qemu.

I have certainly never separately installed anything in order to get the display spice-server running successfully.

---

### Post by MAFoElffen on 2023-05-28
What functionality do you think you would need by installing something additional to a VM Guest in KVM? "Guest Additions" is specifically VirtualBox. 

I'm wondering why you think you need to install a Guest Additions kind of utility in KVM. There is a Virtio Drivers Utility for Windows types of KVM VM guests...

---

