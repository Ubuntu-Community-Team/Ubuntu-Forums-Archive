---
title: "VMWare server / Openfiler NFS"
date: 2008-09-03
forum: Virtualisation
---

### Post by TheGameAh on 2008-09-03
Hi guys.

I put this also in the server forum.  Perhaps it should have gone here first.

We're a small shop, so nothing fancy.  Some files servers, an Exchange 2003 box, licensing server for Solidworks, etc.  Trying to keep things relatively simple, but also want to try some new things. (if that makes any sense).

Not sure if this is even possible in my environment, but wanted to "decouple" the server storage from the hardware.  Basically, what I was looking to do is create a relatively large NFS datastore (500 gigabyte to 1 terabyte, using Openfiler 2.3 NFS).  And simply have all my VMware images on it, with a tiny Debian installed mounting the NFS share and running VMWare Server.  Every single thing I've studied says that in order to achieve what I'm trying to do, you should really use an iSCSI storage or Fiber.  That's definitely overkill for what I'm trying.  Is anyone at all running something along my lines, VMWare server with a central NFS store?  If so, how many VMs/how big are they?  

This might not even be possible.  I could always just run separate server with local storage, but the idea of a central store appeals to me.  If a connecting server breaks, just take another server with extra ram and point it to the central store temporarily.  A lot of benefits.

---

### Post by GrammatonCleric on 2008-11-12
Howdy TheGameAh,

Well actually hosting VMs via NFS is very possible and in some circles it's the preferred method of provisioning storage for vmware.  At our office we have a couple Netapp clustered FAS3050s, one production the other at our DR site.  After designing, planning, purchasing and rolling out our VMware ESX environment to use FC for our production and iSCSI for DR I read several articles from both VMWare and Netapp engineers stating that NFS was far better for provisioning vms to esx hosts. Here's one [**[COLOR=Sienna]article[/COLOR]**]("http://storagefoo.blogspot.com/2007/09/vmware-over-nfs.html"). 



Not that I'm telling you not to use debian or ubuntu but you do know that [**[COLOR=Sienna]esxi is now free[/COLOR]**]("http://www.vmware.com/products/esxi/"). 



In the year since we purchased our ESX lic we've started switching to ESXi to save costs.  Its basically the something as ESX it just doesn't have a service console and the install is so easy it's a joke.

Hope this helps,

-GC

---

