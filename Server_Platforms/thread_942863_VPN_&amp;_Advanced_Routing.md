---
title: "VPN &amp; Advanced Routing"
date: 2008-10-09
forum: Server Platforms
---

### Post by code0 on 2008-10-09
I've been hitting my head on a wall over this.. I have a VPN server that has both an internal and external interface. I want any traffic that is coming from the VPN (ppp0 - it's L2TP IPSec based) to go to the default gateway of the internal network so the VPN can see all the subnets that are available - not just the ones the VPN server itself can see. I'm guessing I need some ip route mojo to get this working, but I'm not quite sure what it is. Here's the setup of the VPN server:

eth0 (internal):
IP: 10.99.99.25/24

eth1 (external):
IP: 1.2.3.4/24
Gateway: 1.2.3.1

ppp0 (L2TP VPN):
IP: 172.16.45.1
Assigns 172.16.45.51-250 to clients

Internal gateway IP: 10.99.99.1

So, I guess the best way to rephrase it is I want traffic coming out of ppp0 to have a next hop of 10.99.99.1 while everything else isn't touched.

BTW, I'm running Ubuntu 8.04.1 x64

---

### Post by Robstarusa on 2008-10-10
> **code0 said:**
> I've been hitting my head on a wall over this.. I have a VPN server that has both an internal and external interface. I want any traffic that is coming from the VPN (ppp0 - it's L2TP IPSec based) to go to the default gateway of the internal network so the VPN can see all the subnets that are available - not just the ones the VPN server itself can see. I'm guessing I need some ip route mojo to get this working, but I'm not quite sure what it is. Here's the setup of the VPN server:

eth0 (internal):
IP: 10.99.99.25/24

eth1 (external):
IP: 1.2.3.4/24
Gateway: 1.2.3.1

ppp0 (L2TP VPN):
IP: 172.16.45.1
Assigns 172.16.45.51-250 to clients

Internal gateway IP: 10.99.99.1

So, I guess the best way to rephrase it is I want traffic coming out of ppp0 to have a next hop of 10.99.99.1 while everything else isn't touched.

BTW, I'm running Ubuntu 8.04.1 x64

How about adding in a static route?

---

### Post by code0 on 2008-10-10
I want to avoid that if possible. I want to keep all routes on the core router of my network. I could do static routes, but I'd have to maintain them too..

---

### Post by koenn on 2008-10-10
i'd opt for a static route as well. It's just the one and if you document it as part of your vpn setup, it probably is quite maintenance free afterwards.

Possibly running a routerprotocol that can grab routing info from your main router would also work, but that sounds more complex (and I have no experience with it)

---

### Post by koenn on 2008-10-12
happened to  be looking at man iptables (for an unrelated issue) and noticed something that might help. 

[http://iptables-tutorial.frozentux.net/other/iptables.html](http://iptables-tutorial.frozentux.net/other/iptables.html)

look at the target "ROUTE" and its params : you can override the kernel routing tables and assign a gateway or out-interface based on a match, so you could maybe do something like```

iptables  .... -i ppp0 -j ROUTE --oif eth0

#or possibly
iptables  .... -i ppp0 -j ROUTE --gw 10.99.99.25
#or maybe that should be
iptables  .... -i ppp0 -j ROUTE --gw 10.99.99.1

```and let the router take it from there

---

