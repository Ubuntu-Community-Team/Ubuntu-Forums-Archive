---
title: "Home server - help with dhcp and dns"
date: 2007-12-26
forum: Server Platforms
---

### Post by berbs on 2007-12-26
I am trying to setup a home server to act as a router on my internal network. I need some pointers with the network configurations. I have three NIC interfaces:

[LIST]
[*]eth0: connected to the cable modem (dhcp client)
[*]eth1: connected to a linksys wireless bridge
[*]eth2: directly connected to a mac (1Gb)
[/LIST]

Questions:

[LIST=1]
[*]I would like eth1 and eth2 to serve dynamic IP addresses, do I need to bridge the two interfaces? Is there a link where to find more information?
[*]What do I need to do to be able to be able to address all the network clients by name instead of IP? All the local computers are running macos X and use dhcp.
[/LIST]

---

### Post by doogy2004 on 2007-12-26
sounds like you need smoothwall [http://www.smoothwall.org/](http://www.smoothwall.org/)  give it a try, it is easy to setup and use.

---

### Post by cammj on 2007-12-27
What you want to do is highly achievable

What you want to do is to install dhcp server and bind on your server. I would then suggest using something like webmin to configure these services for the novice user.

For your DNS setup, I suggest creating a zone ending in .local, say myhome.local. You can then set all your machines to point to the DNS server and you can then resolve them with names for instance computer1.myhome.local.. Setting a DNS prefix on these computers will make this even simpler, by allowing you to just type "computer1" instead.

As for the router part, there is a great guide on the ubuntu documentation website located at [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Good Luck!

---

### Post by koenn on 2007-12-27
> **berbs said:**
> I am trying to setup a home server to act as a router on my internal network. I need some pointers with the network configurations. I have three NIC interfaces:

[LIST]
[*]eth0: connected to the cable modem (dhcp client)
[*]eth1: connected to a linksys wireless bridge
[*]eth2: directly connected to a mac (1Gb)
[/LIST]

Questions:

[LIST=1]
[*]I would like eth1 and eth2 to serve dynamic IP addresses, do I need to bridge the two interfaces? Is there a link where to find more information?
[*]What do I need to do to be able to be able to address all the network clients by name instead of IP? All the local computers are running macos X and use dhcp.
[/LIST]

1- you don't need to bridge, you can have the dhcp server give out leases on both interfaces. 

2- use dns

you can probably combine 1 and 2 by using dnsmasq
note that all of this has nothing to do with routing. You need to set that up separately. ee cammj's link

---

### Post by berbs on 2007-12-29
Thanks for the feedback. I followed the advice and did not bridge the two interfaces. It seems to me that creating a bridge has some advantages such as having one subnet for all interfaces and the ability to easily add more interfaces to the bridge, including wireless ones. Any thoughts?

---

### Post by koenn on 2007-12-29
it depends on your network design, and the requirements that led to that design.

If you want or need everything in one network, bridging might be a solution, but is most cases a simple switch will work just as well. 

If you want to divide the hosts in separate networks, eg trusted vs. untrusted, wired vs wireless, or any other division that suits your needs, separate networks are probably the preferred choice, because traffic beyond the border of a network needs to be routed, and can be filtered at network level ( firewall, ...)

---

### Post by berbs on 2007-12-31
I ran into another interesting problem and I can't seem to find information on how to address it. My router now works great. Any client directly connected to the box gets access to the net and fast name resolution. 

The problem comes when I connect my linksys wireless router into the linux router. It gets the right IP, dns and gateway entries, however access to the net is dog slow. 

I suspect some missing masquerading rules or something of the sort, but help would be greatly appreciated. The linux router provides addresses in the range 192.168.1.200-249. The linksys router provides addresses in the range 192.168.3.30-50

thanks

---

### Post by berbs on 2007-12-31
found the problem... The linksys router had some leftover dns configuration and was sending a non existing address first. the client request had to time out before getting to the valid dns server. duh!

---

