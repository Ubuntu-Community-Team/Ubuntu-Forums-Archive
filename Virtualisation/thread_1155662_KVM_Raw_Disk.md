---
title: "KVM Raw Disk"
date: 2009-05-11
forum: Virtualisation
---

### Post by carrotis on 2009-05-11
I have a question how to boot KVM using raw disk image.
 
example.
 
    /dev/sda : installed Ubuntu (bootable)
    /dev/sdb  : installed Customized Ubuntu (bootable)
 
    I make raw disk image 'linux.img'
    
    dd if=/dev/sdb of=linux.img bs=1024
 
 
Using 'linux.img' raw disk , I want boot on KVM.
 
 
I try to 
 
     virt-install command...  I can't
     kvm -m 512 -hda linux.img -boot c   ... I can't
 
Plz help me.

---

### Post by bodhi.zazen on 2009-05-11
Try converting the raw image to qcow :

```
qemu-img convert linux.img -O qcow2 linux.qcow
```

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

---

