---
title: "Server+2 gateways? Its posible?"
date: 2010-10-06
forum: Server Platforms
---

### Post by eufran on 2010-10-06
Hello i have two gateways of internet:

GW 192.168.0.1 -------
                      ---SERVER ----- LAN 192.168.1.x
GW 192.168.0.2 -------

How can i say to ubuntu server 10.04 that the gateway of the server (/etc/network/interfaces) is the 192.168.0.1, but the gateway of the squid is the 192.168.0.2

It is posible??

Thanks

---

### Post by endotherm on 2010-10-06
it is possible but probably not with the network hardware you have. 
when networks have redundant paths, they use routing algorithms like RIP, OSPF, and IGRP to determine which of the available routes is optimal. this way, even though there are multiple paths only one is used at a time to prevent routing loops from counting to infinity. 

on what basis would you like to choose which gateway is used?

---

### Post by BkkBonanza on 2010-10-06
I'm assuming you mean that you want to route squid requests out thru the second gateway...

You would need to add an iptables rule to mark packets that are owned by squid and then routing rules to direct them to the second gateway.

Briefly, for example,

iptables -t mangle -I OUTPUT -m owner --uid-owner squid -j MARK --set-mark 0x1

ip rule add fwmark 0x1 table 101 pref 101

ip route add default via 192.168.0.2 dev eth0 table 101

Here is a [post]("http://www.mail-archive.com/shorewall-users@lists.sourceforge.net/msg05628.html") where I found this info and it has more detail, except you don't need anything regarding shorewall.

---

