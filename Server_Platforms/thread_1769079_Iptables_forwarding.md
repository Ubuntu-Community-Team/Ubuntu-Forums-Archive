---
title: "Iptables forwarding"
date: 2011-05-27
forum: Server Platforms
---

### Post by turki_00 on 2011-05-27
Hi,

am using a Ubuntu box a gateway to other PCs and I need to apply some rules before a pass those packets from the internet to the internal network.


In the iptables for the gateway Ubuntu machine:

First, I want to pass all incoming traffic to NFQUEUE for some pre-processing

iptables -I INPUT -p tcp --dport 80 -j NFQUEUE
iptables -I OUTPUT -p tcp --sport 80 -j NFQUEUE

then, for the forwarding process

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination InternalIP:80
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE


the problem is that the forwarding is ALWAYS happening before examining the packets at the NFQUEUE

my question regarding the sequence of processing iptables chain. How can i apply a chain before the NAT table prerouting chain?

Thank you,

---

### Post by turki_00 on 2011-05-30
Ok, Let me try to clarify my question,

How can I inspect http traffic (via NFQUEUE) before I forwarded it to another IP

My current iptables:

iptables -L

iptables -I INPUT -p tcp --dport 80 -j NFQUEUE
iptables -I OUTPUT -p tcp --sport 80 -j NFQUEUE


iptables -L -t nat

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination InternalIP:80
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

---

