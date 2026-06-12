---
title: "Internet on Ubuntu LTSP"
date: 2010-01-22
forum: Server Platforms
---

### Post by Silveira on 2010-01-22
Hi guys. We are using in a few labs the Ubuntu LTSP solution.

In each lab we have a server with Ubuntu (9.04) Desktop (Alternate Edition) that we installed using the option LTSP Server. It has worked just out of the box, each lab has about 15 diskless machines thinclients.

Each server has two network cards, one linked to the thinclients and the other to a router that is linked to a ADSL modem. The Ubuntu LTSP Server is serving DHCP in our internal network and machines that are enable of do network book are working well, but, when we have a laptop that wants just to connect on Internet, it gets a valid IP and everything but doesn't connect on Internet.

In our past solution, Debian+LTSP+a few things, this used to work. 

How you guys that are using Ubuntu LTSP out of the box are dealing with this? How Ubuntu LTSP allow to use regular internet through it?

---

### Post by scrooge_74 on 2010-01-22
You need to do ip forwarding

echo 1 > /proc/sys/net/ipv4/ip_forward

Did you enable NAT? iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth1 -j ACCEPT

You could use a firewall interface to manage this last part

---

### Post by Silveira on 2010-01-22
Thanks scrooge_74, I'll try this and then I'll post if worked or not.

---

### Post by scrooge_74 on 2010-01-22
The iptables config is in several places, [here]("http://www.bctes.com/nat-linux-iptables.html") is one of those places

---

