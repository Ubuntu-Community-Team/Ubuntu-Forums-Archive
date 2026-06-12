---
title: "Unusual 4 interface routing question, advice needed."
date: 2010-07-30
forum: Server Platforms
---

### Post by mckinleytabor on 2010-07-30
I need some gentle route advice for my Ubuntu server/router/nat box. 

I am the part time sys-admin for a network that has some "odd" security requirements. Basically within the same network the machines need to have complete access to each other, however certain things on this network are not permitted to access have unfettered access to the internet. Those devices do get access to the internet, but it must first pass through a VPN to an offsite part of the corporate structure higher on the food chain than us. 

Because not all of these "devices" are "computers", loading individual VPN software is not possible. 

How we have done this in the past is to have a small block of IP addresses from our ISP rather than a single address. On one of our external IPs we setup our normal router which handles the bulk of our internet traffic, DHCP, NAT, and any port forwarding we need done. On a second external IP we have setup a completely separate Linux box for our special routing needs. This box is setup similarly to the first, except it does not have DHCP running on it (because two DHCP servers causes chaos on a network :) ). We have a PPTP client running on this box that links into the VPN server, and then we simply route all traffic for this box over the VPN. 

For those devices that can have unfettered access to the internet, we give them the gateway address of the first box. 

For those devices than cannot have unfettered access to the internet, we give them the gateway address of the second box.

…and we all lived happily ever after…. until we got a new manager/overseer. 

New management has determined that the only thing that will save the company from economic ruin is if we eliminate the cost for the small block of IP addresses.

To minimize my overall workload I would like to mirror the existing infrastructure as much as possible. To that end I now have a shinny new Ubuntu 10.04 server setting on our single external IP address. This server has several ethernet cards in it (just in case, though I'm not apposed to a plan that uses virtual interfaces), here how it breaks down:

eth0 ----> Single ISP fixed IP address 
eth1 ----> 192.168.1.1 - Normal network gateway
eth2 ----> 192.168.1.2 - Normal "special" gateway used by the things that can have unfettered access to the internet
ppp0 ----> PPTP client interface with IP address assigned when connected (almost never the same one twice)

(Side note, eth1 is part of an bridge br0 as is interface tap0. The interface tap0 is part of a level 2 OpenVPN link to an outside office that connects to us. Because it's level 2 with no IP routing, I don't think it would interfere with anything else. )

Each of the parts of this pie have been tested on the new box. I have access to the two internal IP address, NAT works, iptables work, PPTP works, and I can adjust the route tables to send ALL traffic over the VPN.

What I would like to do is ONLY route traffic for eth2 over ppp0. Traffic coming from eth1 and all the box's native traffic can run over eth0. 

I can conceptually see how this would work in my head, but my "route foo" is weak, and I just can't think of the right search terms for Google. (searching for "stupid manager just likes to change things to give the illusion of progress" does not net any useful results).

I have found some tutorials on load balancing which seems sorta like what I'm trying to do, but if the ppp0 interface collapses all traffic for devices using eth2 as the default gateway needs to stop for security purposes. It seems that I must create two routing tables, but I have little experience in this area. Any help/advice would be appreciated. Thanks!

---

