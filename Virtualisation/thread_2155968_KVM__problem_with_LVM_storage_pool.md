---
title: "KVM : problem with LVM storage pool"
date: 2013-06-20
forum: Virtualisation
---

### Post by dada941 on 2013-06-20
Hello,

I've created a disk pool for KVM, on a LVM Volume Group. Then I try to launch a new VM with 
```

# virt-install --name=MyVM\
--ram=6112 \
--cdrom=/var/lib/libvirt/images/ubuntu.iso \
--os-type=linux \
--disk pool=vg1,size=50,cache=none \
--graphics vnc \
--noautoconsole \
--hvm

```
It creates the Logical Volume in the VG and launches the VM install process. The virtual machine detect the correct size of the disk (50G), but fails to write when creating the partition (input/ouput error).
I look at the LV's size on the host, it's 4M. It looks like it won't increase size.

If I launch the VM with the option **sparse=false **to the disk then the LV size on the host is 50G and the VM install just fine.

Any idea how I can get dynamic size for the Logical Volume working ?

Cheers,

---

### Post by dada941 on 2013-06-20
Answering to myself :)

After a little more digging, it seems that the thin provisioning in LVM2 is still in experimental stage. 
It will not work on Ubuntu 12.04. :(

---

