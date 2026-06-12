---
title: "iptables &amp; VPN client"
date: 2012-01-12
forum: Security
---

### Post by LordRichardRahl on 2012-01-12
Hi,

I'm trying to set up iptables rules on a desktop machine that is acting as an IPSec/L2TP VPN client.  I would like to be able to prevent all outbound traffic that does not fall into any of the following categories:
[LIST]
[*]DHCP packets (to allow connection to the IP network)
[*]ISAKMP packets to allow set-up of the IPSec connection
[*]ESP packets that transport the data
[/LIST]
My internet searches bring up lots of hits for a gateway machine to allow this type of traffic to route through it, but not to enforce this when the firewall is on the source machine.

I have tried the following iptables rules:
```
iptables -A OUTPUT -p udp --sport 67:68 --dport 67:68 -j ACCEPT
iptables -A OUTPUT -p udp --sport 500 --dport 500 -j ACCEPT
iptables -A OUTPUT -p esp -j ACCEPT
iptables -A OUTPUT -j DROP
```
These rules allow the DHCP and ISAKMP packets through, and in fact IKE completes and the IPSec connection gets created (checked via wireshark at the remote end).  ESP packets get dropped.

From experimentation with a few different rules, it appears that iptables is dropping all packets attempting to leave, presumably because they are entering the IP stack as whatever they are at source, only becoming ESP packets as they traverse the IPSec layer.

Is there any way to achieve my goal, or am I trying to do something that simply is not possible with iptables?

Any help is gratefully received.

---

