---
title: "IPTABLES - Allow Internal HOST with Public IP through Firewall"
date: 2008-06-30
forum: Server Platforms
---

### Post by redmondmj on 2008-06-30
Hello:

I am new to IPTABLES. I have setup and Ubuntu 8.04 Server running
ebox. It is running DHCP (192.168.1.0-250), NAT, DNS, Squid
Transparent Proxy. All of the firewall rules were configured using ebox's firewall module.

Basic setup:
Eth0 - external interface 12.32.12.2 (GW 12.32.12.1) - Internet

Eth1 - internal Interface 192.168.1.254

I have a host on the internal network that I need to assign a public
IP to allow unrestricted access to the internet. 12.32.12.3...

I have been told that ebox can not configure this for me and I have no
idea what I'm doing in IPTABLES. From what I have read it looks like I
should be able to setup something in PREROUTING and POSTROUTING to
allow me to do this?

Any help would be greatly appreciated!!!

Thanks,

---

### Post by koenn on 2008-06-30
If you give a host in your 192.168.1.0 network a different, "public" IP address, it will no longer be part of the 192.168.1.0 lan, you do understand that, don't you ? 

I'm thinking you might mean that you want NAT/ Masquerading i.e. that, from outside the LAN, that host will *appear* to have a a different IP address than when looking at it from the LAN, but I don't quite understand how that would help in giving it unrestricted internet access. 

Maybe you have to clarify a few things first.

---

### Post by redmondmj on 2008-06-30
I do understand that the host will no longer be accessible on the 192.168.1.0 network once I assign it a real IP. This host is actually a client will be running their own firewall and some vpn stuff.

NAT is already working on the internal network. All hosts on the 192.168.1.0 network (obtained by DHCP) are able to access the internet through the external interface.

I'll be more than happy to clarify anything, please do hesitate to ask... I'm new to this so just I'm not sure what exactly would be helpful to provide.

Thanks,

---

### Post by koenn on 2008-06-30
you say . 

> **All** hosts on the 192.168.1.0 network are able to access the internet through the external interface.

but you also say 
> I have a host on the internal network that I need to assign a public
IP to allow unrestricted access to the internet

The way I understand this, is that this host already has internet access, just like all the others. What's the difference then ?

---

### Post by redmondmj on 2008-06-30
This host can get connectivity to the internet if it is part of the 192.168.1.0 network, but I need to be able to assign this particular host, that happens to be within the internal network and connected to the internal interface, with public IP address other than that of the external interface. I have done this in the past with software DMZ's and by adding the IP to an arplist, however I am not familiar with how to make this work in Ubuntu.

---

### Post by redmondmj on 2008-06-30
I think the main problem is eBox is doing NAT with the incoming connection. It may disable NAT when destination/source is that public IP host. I think that this can still be done by entering an iptables rule in "PREROUTING" and "POSTROUTING" chains in "nat" table. I don't know exactly which rule to insert though...

Maybe I'm mistaken?

---

### Post by koenn on 2008-07-01
> **redmondmj said:**
> I think the main problem is eBox is doing NAT with the incoming connection. It may disable NAT when destination/source is that public IP host. I think that this can still be done by entering an iptables rule in "PREROUTING" and "POSTROUTING" chains in "nat" table. I don't know exactly which rule to insert though...

Maybe I'm mistaken?

Let's get this straight : the system that is running IP tables is not the server we're discussing, it's this "eBox', some appliance running linux and acting as a router/firewall, right ?

It sounds strange that you'd be doing NAT on incoming connections. Are you sure your not actually NATing outgoing connections ? If you NAT incoming connections, what are they NATed too ? 


If I understand your setup correctly, you probably need to do something like this : 

create an alias on the LAN-interface of your router, and give it an address in the netwerk of the server's public IP addres. This means that the LAN IF will have 2 IP addresses, or rather, that you'll have two instances of eth1, i.e. eth1:0 and eth1:1. The router will be able to (or has to be told to) route traffic for the public accessible server over its eth1:1 (or via the 2nd address of that interface) while trafic for 192.168.1.x routes via eth1:0 or 192.168.1.254.


I can imagine there might be an alternative involving DNAT, but I can't really see how that should be done.

---

