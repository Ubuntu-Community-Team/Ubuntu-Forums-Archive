---
title: "IPTABLES NAT frustration"
date: 2008-09-23
forum: Security
---

### Post by hattriq27 on 2008-09-23
I have a system that I want to make a firewall it has two interfaces.  ETH0 is static wan, ETH1 is static LAN.  I only want to open SSH to a box behind the firewall in the LAN and have the LAN have outbound access.

Here is the silly part, I have IPTABLES configured so I can SSH into the server I want.  I can't get anything on the LAN to route out through the firewall.

Can someone paste a simple snipet of IPTABLES which will allow systems in the LAN to route out?

I have tried these so far;

iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to **extIP**

iptables -A POSTROUTING -t nat -o eth0 -s 192.168.1.0/24 -d 0/0 -j MASQUERADE

iptables -A POSTROUTING -t nat -o eth0 -j MASQUERADE

iptables -A POSTROUTING -t nat -o eth0 -s 192.168.10.0/24 -d 0/0


And here are my FORWARD rules:

iptables -A FORWARD -t filter -o eth0 -m state \
         --state NEW,ESTABLISHED,RELATED -j ACCEPT
 
iptables -A FORWARD -t filter -i eth0 -m state \
         --state ESTABLISHED,RELATED -j ACCEPT

---

### Post by hattriq27 on 2008-09-23
Ok I figured it out:

iptables -t nat -A POSTROUTING -o eth0 -j SNAT \ 
--to-source $WAN_IP

worked

---

