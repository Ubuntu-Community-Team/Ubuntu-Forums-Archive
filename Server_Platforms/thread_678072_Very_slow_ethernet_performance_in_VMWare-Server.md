---
title: "Very slow ethernet performance in VMWare-Server"
date: 2008-01-25
forum: Server Platforms
---

### Post by AlrikvomFluss on 2008-01-25
Hi there,

currently I try to setup a new home-server. What I want should be simple:
a server with 3 virtual systems: a firewall+router, a fileserver and a sunray-server.

I decided to use Ubuntu-Server, running on a Athlon X2 with 2x 2,0Ghz, 2GB Ram and 2 nics.
My plan was to use one nic for external network (WAN) and one for internal. Due to the fact, that it's not possible to setup XEN /w dynamic CPU-clockspeed, I want to use VMWare Server.

What I did: 
Install Ubuntu, upgrade and then install VMWare Server from the repository. Afterwards, I setup the two bridged ethernets (vmnet0 + vmnet2).
For the fileserver I created a VM /w 512MB, both cpus, Ubuntu-server and nfs-kernel-server. But that's the point, where I stucked.
Trying to access the VM via ssh needs at least 2 minutes to connect and the performance via nfs is very bad (3-5MB/s). On the native system I reach ~65MB/s.
Hoping, that this is a problem of my fileserver config, I've setup the firewall/router. Again: very bad ethernet performance :(

Could anybody imagine, where the problem could be? 
Thanks a lot!

---

### Post by AlrikvomFluss on 2008-01-25
Hi,

I posted the same question in the vmware.com forum, where I finally got the following hint:
with the forcedeth driver for nforce, vmware performance usually sucks. the only solution would be the nvidia driver nvnet, which can not be compiled with actual kernels.
so i have to buy a new ethernet card :-/

---

