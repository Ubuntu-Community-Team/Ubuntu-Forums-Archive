---
title: "kvm-img / qemu-img: KVM LVM2 error"
date: 2009-12-16
forum: Server Platforms
---

### Post by unkownworld on 2009-12-16
Hi,

I've Ubuntu 9.10 (server) with kvm support.
I get the following error, when I want to copy a cow image to a lvm2 volume:


[PHP]
kvm-img convert disk0.qcow2 -O raw /dev/mapper/hd3-hd3
qemu-img: Error while formatting '/dev/mapper/hd3-hd3'
[/PHP]

I saw some forum post with mostly the same problem and it should be fixed with qemu 0.11.1. I tested a self compiled 0.11.1 and 0.12-rc1, but I get the same error.

What did I wrong?

---

### Post by unkownworld on 2009-12-17
No one have a solution?

---

