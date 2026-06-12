---
title: "About creating VM"
date: 2010-01-10
forum: Virtualisation
---

### Post by satimis on 2010-01-10
Hi folks,

Host - Fedora 12 64 bit
KVM
AMD 64 Phenom II X4 955
VM - debian-503-amd64

I'm prepared running following command to install VM```

virt-install --connect qemu:///system -n vm10 -r 512 --vcpus=2 -f ~/vm10.qcow2 -s 12 -c ~/debian-503-amd64-netinst.iso --vnc --noautoconsole --os-type linux --os-variant debianlenny --accelerate --network=bridge:br0 --hvm
```

Shall I use: --vcpus=2

OR
--vcpus=4
???

This is a quadcore box. TIA

B.R.
satimis

---

