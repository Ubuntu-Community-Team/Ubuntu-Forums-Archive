---
title: "Moving VM between different hypervisors?"
date: 2020-12-10
forum: Virtualisation
---

### Post by rsteinmetz70112 on 2020-12-10
Is it possible to move an existing virtual guest to a different hypervisor (like from virtualbox to KVM) or is in necessary to reinstall the guest OS?
Can the guest be backed up and restored to a different hypervisor?
I know only one hypervisor can be installed at a time.

---

### Post by QIII on 2020-12-10
If your guest is using a .vdi in VirtualBox, you can convert it to a .qcow2, then set up a VM in KVM to use it.  I would first make sure to have a backup/snapshot or what have you.

You might have to install a couple of things:

```

sudo apt -y install qemu-kvm libvirt-bin virtinst bridge-utils

```

And then do the conversion

```
qemu-img convert -f vdi -O qcow2 path/to/whatever.vdi newpath/to/whatever.qcow2 
```

---

### Post by ajgreeny on 2020-12-10
I have done more or less what QIII talks about, though with slight differences, many times with complete success.

I followed the information on the page at [https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2](https://dev.to/guinuxbr/convert-ova-to-qcow2-48f2)
First I exported the vdi of many Linux VMs to an .ova then extracted the .ova to the two files it contains and finally used the ***qemu-img convert*** command to convert the extracted .vmdk file to a qcow2 file which imports into ***virt-manager*** very quickly and easily.
I have not tried the direct conversion from .vdi mentioned by QIII but it is very quick to convert the way I show, and my linked site shows

Definitely worth doing if you install the full kvm/qemu infrastructure, in my case adding virt-manager, a simple gui for managing VMs in kvm/qemu.
In my experience, having used virtualbox a lot in the past, VMs generally run much faster and smoother in kvm/qemu that they do in VBox, though your mileage may differ, of course.

---

### Post by TheFu on 2020-12-10
Yes. Remove the guest additions first!

I've moved by converting the storage file using qemu-img into a nicer format for kvm, placed that file where it needed to be in /var/lib/libvirt/, then create an empty VM inside virt-manager, pointing the storage file at the location and ensring the network bridge (or pci NIC) desired is passed thru.

I think we could keep VDI if desired.

Any fake hardware devices that aren't supported in qemu would need replacing, obviously.
Linux VMs are pretty easy.
Windows VMs usually demand a fresh install for license reasons. After all, the entire motherboard (virtual) was changed.

---

### Post by rsteinmetz70112 on 2020-12-10
Thanks.

---

