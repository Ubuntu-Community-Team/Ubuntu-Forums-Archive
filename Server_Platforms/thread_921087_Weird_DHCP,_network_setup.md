---
title: "Weird DHCP, network setup"
date: 2008-09-15
forum: Server Platforms
---

### Post by DHag on 2008-09-15
I have just done a new install of Ubuntu 8.04 LTS Server for the 4th time. Everything goes without a hitch, but the DHCP behaviour and IP address assigned to the NIC is all wrong.

I have a DHCP server (Windows 2003) on the network. The address pool is set to 192.168.1.100 - 199. Every machine on the network gets its IP correctly from this server.

During Ubuntu setup, it says it calls DHCP successfully. It never gives me a chance to set up the network manually, which I would like to do for a server. It connects to the Internet fine, and everything works except it will not communicate with any other machine on the network, except with a Putty client. No ping, no traceroute, nothing, because the address it comes up with is 192.168.158.xxx. This is coming from my ISP's DHCP server!

When I set up the network manually to match my own internal network (using either vi or Webmin), then NOTHING works on it. I must go to the console and reset it to DHCP again, then it goes right back to my ISP's DHCP server.

Why is Ubuntu setup going out through my IPCop box to my ISP's DHCP server, when it's sitting right next to my own DHCP server? Plugged into the same hub! And why will setup not allow me to do a manual configuration? And why will nothing work when I do a manual setup? :confused:

---

### Post by wirelessmonkey on 2008-09-15
192.168.x.x addresses are not routed. Since you are obviously behind a home dsl/cable modem and/or home router, the 192.168.158.x address cannot be coming from your ISP.  I suspect MS DHCP misconfiguration.

---

### Post by promodus on 2008-09-16
> **wirelessmonkey said:**
> 192.168.x.x addresses are not routed. Since you are obviously behind a home dsl/cable modem and/or home router, the 192.168.158.x address cannot be coming from your ISP.  I suspect MS DHCP misconfiguration.

[RFC 1918]("http://tools.ietf.org/html/rfc1918")

These addresses are routable. However the address space is reserved for each network. 

An example would be, the addresses would not be used between one companies network to another. 
Another example: It should not forward from your home network to your ISP as to the specification, however you can still do that if you wish, it's just not-to-spec.

---

### Post by Iowan on 2008-09-16
I'm not suggesting you "go for #5", but installing with NIC cable unplugged might force the manual configuration issue.  Another thing to try would be unplugging the internet connection and rebooting the machine to see what address it comes up with. Setting up a static lease in the DHCP server *might* give you the best of both worlds.

---

