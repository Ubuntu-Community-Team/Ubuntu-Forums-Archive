---
title: "kvm configuration - problem adding user to libvirtd"
date: 2017-10-27
forum: Virtualisation
---

### Post by luca-barazzuol on 2017-10-27
Hi,

I'm following this tutorial to install e configure kvm on my ubuntu 17.10:
[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

But when I try to add my user to the group libvirtd I get error as this group doesn't exist.

```
$ sudo adduser `id -un` libvirtd
adduser: The group `libvirtd' does not exist.
```

Maybe the tutorial is obsolete and that group has been renamed?

In my system there are these groups related to kvm/qemu/libvirt:
kvm
libvirt
libvirt-qemu

To which group should I add my user?

Thanks

LK

---

### Post by Dennis N on 2017-10-27
I installed it about a week ago in 17.10, and never added myself to any group. I only installed **virt-manager**, and all the other needed packages came automatically as dependencies. After that, it was ready to use.

---

### Post by deadflowr on 2017-10-27
> To which group should I add my user?

libvirt

---

