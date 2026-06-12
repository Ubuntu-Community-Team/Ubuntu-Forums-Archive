---
title: "Shorewall and VMware Server"
date: 2008-11-10
forum: Server Platforms
---

### Post by Loky on 2008-11-10
Hey!

I've hit a dead end and would greatly appreciate a little help if anyone would kindly guide me in the right direction. 

The setup currently stands with a ubuntu 8.10 server running vmware server with shorewall installed. A virtual machine is running, also 8.10. For the host I've blocked everything except a couple of ports required for administration ect. The virtual machine will be used to host a couple of sites and an email server. The issue I'm having is port forwarding with shorewall. 

I can SSH to the host, and then from there SSH to the guest OS, but I can't SSH directly to the guest OS even with ports forwarding. As soon as I've get a connection to SSH I can sort out the rest of the ports with regards to apache ect.

The guest os is using the NAT connection provided by vm host and shorewall is currently configured to vmnet8 for 'loc', vmnet8 being the NAT interface device.

Any clues anyone or am I being dense and missed something vital. 

Many thanks!

---

