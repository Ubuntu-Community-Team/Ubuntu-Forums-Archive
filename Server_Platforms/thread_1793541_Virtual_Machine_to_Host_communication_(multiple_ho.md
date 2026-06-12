---
title: "Virtual Machine to Host communication (multiple hosts)"
date: 2011-06-29
forum: Server Platforms
---

### Post by YouBuntToo? on 2011-06-29
Hi!

My setup involves two hosts each running a few virtual machines. I'm using kvm/lib-virt(virt-manager) to run the VMs. The hosts are running ubuntu 11.04. The hosts are both going to the same router, gateway, etc.

I want the VMs on host1 to be able to 'see' host2 and be able to see the VMs running on host2 (I want to be able to ping them, transfer files between them, etc) . Does this involve bridged networking?

I've already tried setting up a bridged connection, but I can't get the VMs to connect to the internet or to see the other parts of the network. Just want to know if I'm on the right track.

Thanks

---

