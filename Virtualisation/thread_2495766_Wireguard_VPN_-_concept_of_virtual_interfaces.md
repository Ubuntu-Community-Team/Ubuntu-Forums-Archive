---
title: "Wireguard VPN - concept of virtual interfaces"
date: 2024-02-29
forum: Virtualisation
---

### Post by aljames2 on 2024-02-29
I have a working remote access vpn set up for accessing a Nextcloud server at home.  All hosts running Ubuntu server 22.04.  So, I don’t have a question to fix anything but I am looking for a better understanding of how the vpn tunnel virtual interfaces really work, in particular related to their IP addresses.

I understand that all clients and the server each must have a tunnel interface IP address.  These addresses do not seem to be related to any “real network”.

The Wireguard tunnel network must not conflict with a real network and does not need to be within a real network or subnet.  This blows my mind :)

In my case, I have a real subnet at 10.8.10.0/24, and this subnet is where WG & NC live.  Nothing else.  Yet, my WG tunnel IPs are “made up”, all on a fake subnet, 10.0.8.0/32.  I have no such subnet on any physical network anywhere.  What is the point of fictitious IP addresses, unless it is a secret virtual network that only the WG hosts all understand.  Weird, but I’m still learning..

---

### Post by TheFu on 2024-02-29
Routing.  Routing works based on subnets.  If the subnets aren't different and the metric lower for a specific route, then the wrong route will be used and traffic won't flow.  This is why using the same subnets for the target LAN and the client LAN don't work.

Say your home LAN is 192.168.1.x/24 and you are in a cafe with free wifi that has the same subnet of 192.168.1.x/24.  Devices on the same subnet don't go through a router.  They should be able to communicate directly over ethernet just using ARP/MAC tables.  By having different subnets, all traffic knows to go through the router.  If a VPN is enabled, then the VPN metric (priority) needs to be lower than the default route without the VPN running. This way, all traffic will be sent over the VPN and not over the default route.

Clear?

Episodes 25-29 of Security Now! podcast explain "How the Internet Works" ... which is mostly about routing between different networks.  Well worth understanding.

---

### Post by aljames2 on 2024-02-29
> **TheFu said:**
> Say your home LAN is 192.168.1.x/24 and you are in a cafe with free wifi  that has the same subnet of 192.168.1.x/24.  Devices on the same subnet  don't got through a router.  They should be able to communicate  directly over ethernet just using ARP/MAC tables.  By having different  subnets, all traffic knows to go through the router.  If a VPN is  enabled, then the VPN metric (priority) needs to be lower than the  default route without the VPN running. This way, all traffic will be  sent over the VPN and not over the default route.


Thanks TheFu.  This does make sense how you describe it. I see now i need to learn more about the layers & priorities involved in packet handling.

> **TheFu said:**
> Episodes 25-29 of Security Now! podcast explain "How the Internet Works" ... which is mostly about routing between different networks.  Well worth understanding.

I will listen to these, started the first one already.  thanks again for suggesting them.

---

