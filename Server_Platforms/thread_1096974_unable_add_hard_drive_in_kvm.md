---
title: "unable add hard drive in kvm"
date: 2009-03-15
forum: Server Platforms
---

### Post by AkuKalle on 2009-03-15
I have KVM running and created virtual machine called file. I want to add hard drive in file what is connected in host. so tried few commands

virsh # attach-disk file /dev/sdc sdb

virsh # attach-disk file /dev/sdc sdb --driver phy

virsh # attach-disk file /dev/sdc sdb --driver file

virsh # attach-disk file /dev/sdc sdb --driver tap

every time file don't see the disk and when start file i get error

libvirtError: internal error unsupported driver name 'phy' for disk '/dev/sdc'

So something is wrong in driver but i don't know what:(

---

