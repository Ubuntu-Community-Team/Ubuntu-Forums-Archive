---
title: "Best VMware format for converting to kvm?"
date: 2013-06-26
forum: Virtualisation
---

### Post by 1clue on 2013-06-26
Hi,

What is the most reliable image format/type of VMware image to convert to KVM?

I have a Mac running a couple VMs using Parallels.  I want them all moved to KVM and/or QEMU as appropriate.  Some are Linux, but there are a couple Windows images and I don't want to mess up the licenses.

I've tried all sorts of direct conversion using kvm-img, with no luck.  The error is always the same, "disk not bootable".

Now I'm going to try converting from Parallels to VMware, and then VMware to KVM.  I've heard that VMware converts Parallels images pretty much automatically.

If I have any control over the VMware format, I'd like to know what works best.

Thanks.

***Edit:** I started this process here: [http://ubuntuforums.org/showthread.php?t=2155932](http://ubuntuforums.org/showthread.php?t=2155932) but that thread got a bit sidetracked.*

---

### Post by CharlesA on 2013-06-26
This is a few years old, but it be helpful:
[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

EDIT: This might be an issue too:

> I could not convert a .vmdk which was using LVM (Fedora).

=/

---

