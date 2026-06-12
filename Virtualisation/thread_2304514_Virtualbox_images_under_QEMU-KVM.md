---
title: "Virtualbox images under QEMU-KVM"
date: 2015-11-27
forum: Virtualisation
---

### Post by henryjohn on 2015-11-27
Having installed QEMU-KVM in Ubuntu 14.04, I find it copes very well with an ISO image(or CD/DVD) and even an image created under Xen (on another machine), but not VDI images. I was under the impression that KVM could read VDI images, and that this would be included under the "Import existing disk image" option, but I just get an error -

Booting from Hard Disk
Boot failed: not a bootable disk
No bootable device

yet it was using this option that it loaded the Xen image correctly.

What am I doing wrong?

---

### Post by T.J. on 2015-11-30
If you are using virt-manager, I would double check your boot order, just in case.

Yes, you heard correctly, but if the version you have is a little old, I would advise you to use the VBoxManage tool in VirtualBox to convert the VDI (with any snapshots) to a RAW disk image.  

ex: VBoxManage clonehd sdb.vdi sdb.raw --format RAW

After you do that, you can either use the raw image as is, or convert it to another format using qemu-img 

ex: qemu-img convert -O qcow2 sdb.raw sdb.qcow

However, because some OS's (like Windows) are rediculously sensitive hardware changes, it may refuse to boot when you change the virtual hardware froom Xen or VirtualBox to KVM.  Still, it is worth a try.  You may have to reauthorize, if it is Windows.

---

