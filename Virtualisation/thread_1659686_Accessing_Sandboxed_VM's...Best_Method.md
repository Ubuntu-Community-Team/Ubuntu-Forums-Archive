---
title: "Accessing Sandboxed VM's...Best Method?"
date: 2011-01-04
forum: Virtualisation
---

### Post by IscariotJ on 2011-01-04
Hi,

I'm hoping that I'm posting this to the correct forum.....  I'm trying to configure a number of Ubuntu 10.10 VM's running under VMware in such a manner that I have one that acts as a gateway for the for the others ( which cannot see anything except themselves ), with different NIC's directing traffic to individual VM's.  Basically, I need something along the lines of:

Gateway
    eth0 - 10.50.57.x # Bridged, Used For Admin Of Gateway
    eth1 - 192.168.211.x # HostOnly, 
    eth2 - 10.50.57.x # Bridged,  Inbound Directed to VM1 via eth1
    eth3 - 10.50.57.x # Bridged, Inbound Directed to VM2 via eth1
    eth4 - 10.50.57.x # Bridged, Inbound Directed to VM3 via eth1

VM 1
    eth0 - 192.168.211.x

VM 2
    eth0 - 192.168.211.x

VM 3
    eth0 - 192.168.211.x


I'd appreciate any pointers / assistance.

Thanks

John

---

