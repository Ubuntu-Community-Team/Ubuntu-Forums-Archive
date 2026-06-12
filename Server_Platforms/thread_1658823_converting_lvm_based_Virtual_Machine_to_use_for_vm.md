---
title: "converting lvm based Virtual Machine to use for vmware"
date: 2011-01-03
forum: Server Platforms
---

### Post by tapas_mishra on 2011-01-03
I am using KVM on Ubuntu Server 10.04. and Virtual Machines are running on it in LVM.
I have to migrate some of them to Vmware server.How can I achieve this.
I searched and came across some links but they all talked converting vmdk images to qcow or so.
In this case I have OS in LVM.

[http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/](http://blog.bodhizazen.net/linux/convert-vmware-vmdk-to-kvm-qcow2-or-virtualbox-vdi/)

[http://communities.vmware.com/thread/224712](http://communities.vmware.com/thread/224712)

but any of the above did not helped me.
I also looked at man page of qemu-img and as I understand it should do what I am asking in this thread.
But how exactly should I proceed in this case.Since it is not a file based image (OS running in an LVM which has filesystem in that LVM).
So I am not able to understand what should I be doing to achieve the same.

---

