---
title: "Virtualizing FreeNas on Ubuntu 12.04LTS"
date: 2013-05-17
forum: Server Platforms
---

### Post by ductiletoaster on 2013-05-17
I am building a new server that will have ALOT of harddrive space. My original plan was to simply install FreeNas and forget about it. But then I I realized that perhaps I could instead virtualize FreeNas allowing me to also use the server for more than just file backups but also server testing (LAMP, etc). However I am not sure on the best approach for this.

Server:
12TB drive pool + 32GB SSD for system.

On idea was to install Ubuntu 12.04 LTS with VirtualBox then Run FreeNas as a virtual guest (on the SSD). How would I then give freenas access to the drive pool? Would Ubuntu need something like ZFS to be installed and then just created dynamic virtual disks in FreeNas?

Someone at work recommended something like Xen hypervisor.


My Goals:
Build capable backup solution for my home network.
Create testing environmental for multiple OS systems.
Each of these solutions should not be co-mingled. (I.E. Installing Ubuntu + Samba + ZFS + apache + MYSQL+ blahhaa all in the same environment)

---

### Post by tgalati4 on 2013-05-17
I like Xen as a hypervisor, but it has a learning curve and it requires more configuration than other hypervisors.  Will ZFS run reliably under a VM of freenas?  Who knows?  I have a separate freenas server and I have played with an older version of Xen on an old Dell PowerEdge server.  I've been thinking of doing the same thing, but haven't got around to testing it.  I would have to upgrade to the lastest version of Xen.  There's a lot of development going on in Xen and the other hypervisors.  The hypervisor frameworks seem to be in a state of flux and haven't reached a level of maturity that freenas has for NAS application.  Since there is ZFS support under linux, why would you need freenas at all?

It would be instructive to perform some ZFS performance tests using freenas on bare metal.  You can load it from a USB stick and save the configuration on the USB stick.  Then install Xen, your guest Ubuntu server, and guest freenas server and rerun your tests to see the difference in performance.  Then compare ZFS on the VM Ubuntu server and ZFS on the VM freenas.  

Let us know how it goes.  I would runs some reliability tests before committing important data to the pool.

---

### Post by cprofitt on 2013-05-18
I run FreeNAS in VMWare and it works very well. I use it to front 2TB of disk space that is exposed to the host ESX server via iSCSI. I do not have experience with KVM, XEN or VirtualBox running FreeNAS, but I suspect they would work.

---

### Post by chrisguk on 2013-05-18
> **cprofitt said:**
> I run FreeNAS in VMWare and it works very well. I use it to front 2TB of disk space that is exposed to the host ESX server via iSCSI. I do not have experience with KVM, XEN or VirtualBox running FreeNAS, but I suspect they would work.

I also run FreeNAS with VMware ESXi 5.1, it works super fast, you can use ZFS as if it have real hard disks to use.  Its probably the best and easiest virtualisation platform to deploy.  With that said, you need a dual core machine and the very minimum and crap load of memory.  If you are running FreeNAS as a tiny lab project then you may have to go with a Virtualbox model instead.  If you are lucky enough to have a server at home (like me ;) 32GB RAM 2 x Quad Core Intel CPUs) then take advantage of the virtualisation technology with ESXi.

Im my opinion XEN and KVM are just not worth the trouble.

---

### Post by sandyd on 2013-05-19
Proxmox works with freenas as well
you could just install virt-manager and use KVM as well for a non-web gui-feel

---

