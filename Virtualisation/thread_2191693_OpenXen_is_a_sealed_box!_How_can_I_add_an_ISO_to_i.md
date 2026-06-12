---
title: "OpenXen is a sealed box! How can I add an ISO to install an OS?"
date: 2013-12-03
forum: Virtualisation
---

### Post by jcoles on 2013-12-03
I'm trying to create a VM in openxenmanager. How on earth do I access an ISO to install an OS? There's a LocalISORepository that's empty and no way to find out WHERE this is so that I can copy an ISO file into it. See the problem? Why can't I just browse to the ISO file in my file system? 

What am I missing? Why would something so basic be so (apparently) impossible? It's driving me crazy!

If command line is the only way in, please give me an example.

---

### Post by KillerKelvUK on 2013-12-04
So if OXM is using libvirt (I use KVM so not sure) then the storage pool location is likely /var/lib/libvirt/images (or similar)...drop your ISO's in their and refresh your pool.  I struggled with the very same issue with KVM and Virt-Manager...I'm not 100% but maybe its related to whether you've the potential to use a hypervisor that isn't local to the machine your running the GUI manager on, i.e. how would the hyperviser on a remote machine get access to an ISO you've browsed to from your client...storage pools are common across configured hypervisors and are thus known reachable.

best of luck

---

