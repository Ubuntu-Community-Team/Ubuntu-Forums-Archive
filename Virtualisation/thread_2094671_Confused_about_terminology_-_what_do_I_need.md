---
title: "Confused about terminology - what do I need?"
date: 2012-12-14
forum: Virtualisation
---

### Post by mcarrara on 2012-12-14
I'm not actually sure what to call what I want to do.  Is it cloud computing?  Or is it OpenStack or what?

I have two VMware clusters of three physical servers each.  I am tired of paying annual maintenance fees so I am looking at open source alternatives.  I have used Ubuntu servers for 4 or 5 years so I am familiar with them.  

Questions:
From what I can see if I use Xen or XCP I have to run Cento as the base OS, but I can run Ubuntu as the guest.  Is that correct?

If I want to replace my VMware clusters can it be done with Ubuntu and KVM?  Or do I need additional software?

It appears that Ubuntu and KVM only supports GUI-less guests, that would seem to preclude a Windows server guest or can Windows Core run as a guest?

Thanks

---

### Post by lildigiman on 2012-12-21
Have you tried [ESXi]("http://www.vmware.com/products/vsphere-hypervisor/overview.html")? (From VMWare with no fees whatsoever)

It's what I use for virtual machines, however I've never set it up with a cluster. As far as I know, you can manage load balancing and that's it.

---

### Post by grahams on 2012-12-22
Check out Proxmox 
[www.proxmox.com](www.proxmox.com)

Debian based, kvm and openvz. Supports clusters, great GUI and nearly everything you get with vSphere.

---

