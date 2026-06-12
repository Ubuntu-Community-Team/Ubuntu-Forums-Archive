---
title: "OpenVPN networking problem, can't figure it out, anyone want to take a stab at it?"
date: 2010-08-19
forum: Server Platforms
---

### Post by samosamo on 2010-08-19
This is not the first time I've done this. I have a very good understanding of how this works (VPN, network, Ubuntu/linux, etc) but it's been a few days now and I can't find out where the problem is.  Please just give me a few things to check.

I have a "site-to-site" routed OpenVPN setup that is working 100% as intended as far as the two servers go.  They connect to eachother and they are able to ping and route and everything.  Now I want to get the LAN behind it to use it as a gateway, but I can't.

Here is my network topology:

Site B connects to Site A with OpenVPN.  Site B has a LAN behind it that needs to connect to Site A.

--

Site A:
OpenVPN Server (192.168.1.100) w/ NAT (iptables)

--

Site B:
Router (192.168.2.1) with static route 192.168.1.0/24 gw 192.168.2.100
OpenVPN Server (192.168.2.100)
Client #1 (192.168.2.200)

--
> 
Checklist:
[x] Server A has iptables installed (to MASQUERADE traffic)
[x] Server B has no iptables installed (not needed)

[x] Both Server A and Server B have ipv4_forward=1

[x] Server A pings server B (on both eth0 and tun0)
[x] Server B pings server A (on both eth0 and tun0)

[x] Server A cannot ping hosts behind Server B (this is a good thing, it has NAT)
[x] Server B pings hosts behind server A

[x] Router at Site B has route for Server A's network with OpenVPN Server B as the gateway
[ ] Clients at Site B cannot ping Server A (192.168.1.100) or any hosts behind it (192.168.1.0/24)

Here are the traceroutes:

```

admin@openvpn.siteb:~$ traceroute 192.168.1.100
traceroute to 192.168.1.100 (192.168.1.100), 30 hops max, 40 byte packets
 1  192.168.1.100 (192.168.1.100  53.380 ms  55.470 ms  57.982 ms
admin@openvpn.siteb:~$
admin@openvpn.siteb:~$ dpkg -l | grep iptables
admin@openvpn.siteb:~$

```

```

admin@client1:~$ traceroute 192.168.1.100
traceroute to 192.168.1.100 (192.168.1.100), 30 hops max, 40 byte packets
 1  router.siteb.domain (192.168.2.1)  0.780 ms  1.580 ms  1.987 ms
 2  openvpn.siteb.domain (192.168.2.100)  13.968 ms  13.971 ms  13.932 ms
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


```

---

### Post by samosamo on 2010-08-19
You may also take the router out of the situation at Site B, because if I add a static route for Site A on any client at Site B, it still can't ping any hosts at site A.

---

### Post by brettg on 2010-08-20
Perhaps I am misunderstanding the data you have posted but it looks to me like you have your LAN (192.168.2.100) and WAN (192.168.2.1) interfaces on the same subnet at site B. This would cause a failure to route

---

### Post by samosamo on 2010-08-20
> **brettg said:**
> Perhaps I am misunderstanding the data you have posted but it looks to me like you have your LAN (192.168.2.100) and WAN (192.168.2.1) interfaces on the same subnet at site B. This would cause a failure to route

I think you are misunderstanding.  I never made any mention of my WAN interface because that's on the router and the router is not the problem so I didn't give any details on it.  I'll draw it out like this:

Clients---OpenVPN(192.168.2.100)---Network(192.168.2.0/24)--ISP ...cloud... OpenVPN(NAT)---Network(192.168.1.0/24)

---

### Post by samosamo on 2010-08-20
Fixed. Basic networking stupidity. The solution was to set masquerading on Site B's OpenVPN server also, not just Site A.

---

