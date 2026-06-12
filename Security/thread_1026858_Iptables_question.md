---
title: "Iptables question ?"
date: 2008-12-31
forum: Security
---

### Post by lucloubier on 2008-12-31
Hi !

I am doing a ubuntu 8.04 server/firewall setup and I would like some advice regarding this iptables statement being part of the setup script I run once :

$IPT -A FORWARD -i $WAN -p udp --dport 137:138 -j DROP

Is it dropping any samba broadcast before it gets to the Internet on my wan NIC ? If not, what would be the right statement.

Waiting for some guru advice...

---

### Post by albinootje on 2008-12-31
> **lucloubier said:**
> Hi !

I am doing a ubuntu 8.04 server/firewall setup and I would like some advice regarding this iptables statement being part of the setup script I run once :

$IPT -A FORWARD -i $WAN -p udp --dport 137:138 -j DROP

Is it dropping any samba broadcast before it gets to the Internet on my wan NIC ? If not, what would be the right statement.

Waiting for some guru advice...

With other firewall software I've used (IPF and PF on FreeBSD) you would first block everything, and then selectively open ports.
I don't know about iptables, but wouldn't that make more sense ?

I've looked at two examples here :
[http://lists.netfilter.org/pipermail/netfilter/2004-May/053037.html](http://lists.netfilter.org/pipermail/netfilter/2004-May/053037.html)
[http://www.computing.net/answers/linux/samba-and-iptables-issue/29010.html](http://www.computing.net/answers/linux/samba-and-iptables-issue/29010.html)

And those are following the same method.

If you still want to drop samba on the WAN NIC, but not on the LAN NIC then you could write a specific line for iptables to accept those for the LAN NIC, no ?

---

### Post by koenn on 2009-01-01
> **lucloubier said:**
> Hi !

I am doing a ubuntu 8.04 server/firewall setup and I would like some advice regarding this iptables statement being part of the setup script I run once :

$IPT -A FORWARD -i $WAN -p udp --dport 137:138 -j DROP

Is it dropping any samba broadcast before it gets to the Internet on my wan NIC ? If not, what would be the right statement.

Waiting for some guru advice...
you probably want  ...  **-o **$WAN ...
and the FORWARD chain is only relevant if this machine is a router.

---

### Post by lucloubier on 2009-01-01
That box is indeed doing a router's job !

I will try the "-o" change and let you know if my box still broadcast to the Internet...like this:

kernel: IP fw-in rej eth0 UDP 192.168.7.5:138 192.168.7.255:138

Actually, this is picked up on the WAN side (having another machine doing some traffic snif.

Regards... and Happy New Year !

---

### Post by koenn on 2009-01-01
It doesn't make much sense to just be quoting iptables statements without context. 

If you have LAN where there's windows/samba file sharing going on; you don't want this to leak to the internet (assuming WAN=internet), and you'd block it with " -o $WAN ", i.e. packets going out through the $WAN interface. 
If the router/server itself is also doing samba, you'd do the same on the OUTPUT chain. 

To block access from the internet to your shares, you'd block -i $WAN, i.e. packets coming in through the $WAN interface, on the FORWARD chain for the benefit of your LAN hosts, and on the INPUT chain for the server itself, unless you already have a default policy of reject or drop.

---

### Post by lucloubier on 2009-01-01
koenn,

Do you mean replacing this statement-

$IPT -A FORWARD -o $WAN -p udp --dport 137:138 -j DROP

with this one

$IPT -A OUTPUT -i $WAN -p udp --dport 137:138 -j DROP

?

---

