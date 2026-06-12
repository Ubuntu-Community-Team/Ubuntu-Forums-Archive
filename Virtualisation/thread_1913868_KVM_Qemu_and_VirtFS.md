---
title: "KVM Qemu and VirtFS"
date: 2012-01-23
forum: Virtualisation
---

### Post by derjoerg on 2012-01-23
Hi,

I just try to configure file-sharing with 9p between a oneiric host and a oneiric client (both server).

On the host I created a directory as root and set the permissions to 777. Only if I set the accessmode to "squash" I can create files and folders on the client in the mountpoint. But they are all created as libvirt-qemu:kvm and I'm not able to change this (on the client). If I set accessmode to "passthrough", I'm able to see and DELETE the files and folders but I'm not able to create or modify them.

How can I create files and folders with the respective client user rights?

Thanks for all tips.


Joerg

---

