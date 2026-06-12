---
title: "Looking for info on XEN"
date: 2015-03-15
forum: Virtualisation
---

### Post by Simon_Brazeau on 2015-03-15
I've been playing with XEN Hypervisor for the last few days. I have installed Ubuntu 14.04 LTS followed by the network bridge and XEN. I have ten tested creating and running VM's using XL and using Virt-manager. At this point I have a couple questions.

1. What is the best way to store the image/vm's. I followed directions that shows how to create a LVM and storing the VM's there and the virt-manager just creates a img file. I would like to eventually configure this to have redundancy/failover so that if something happens to the storage, the xen server will switch over the storage location. Is there any documents on this?

2. I know this falls over in the opinion based category, but what are the current tools that work best to create/remove/start etc vm's?

---

### Post by TheFu on 2015-03-16
I found Xen to NOT be as predictable on Debian/Ubuntu as I needed after running it for 4 yrs. Sometimes it would refuse to boot after new kernels were installed. Started moving to KVM beginning in 2010 and have never looked back. KVM performance is usually better than Xen and since KVM is part of the core kernel development, it have many more eyes watching the code, performing regression tests, etc. My Xen experience was with xm, not xl.  

"Best" way to store images is highly subjective and the storage used. If you use SSDs, it doesn't matter - go with qcow2 files (which have to be manually created now, since virt-manager doesn't support creation yet). 
If using a 10G SAN and running only Linux VMs, I'd still use qcow2 files.
If using local spinning disks and you like your customers, raw img files.
If you don't like your customers too much - NFS.

I use virt-manager for the limited number of VMs we have here - fewer than 30 and only 5 physical systems. You can create scropts and connect those to a website if you like.  If that is what you want, might be worth loading up proxmox on a test machine to see how they handled it. It is kvm and openvz.
For simple VM start/stop/reboot/pause/save/restore needs from the hypervisor, virsh is fine. virsh and virt-manager are completely network-ready and don't need to be run on the VM host.

So ... if you don't have a specific need to use Xen, I'd switch to KVM sooner. There are a few reasons to only consider Xen - there's a highly specialized, extremely secure, web server OS that only runs on Xen, for example. For general purpose desktops or servers, KVM has been much less problematic for me.  Just before this reply, another user asked about Xen and I replied there too with slightly different information/background - think you'd like to read that too.

If you need to have 50+ physical VM servers, take a look at openstack. It is a major hassle and there aren't any good upgrade paths.

Regardless - get into devops to manage all these servers.

---

