---
title: "[SOLVED] UFW on bridge interface"
date: 2013-11-20
forum: Security
---

### Post by boshkash1151 on 2013-11-20
I have a bridged interface br0 connecting eth0 and eth1 physical interfaces. eth0 is connected to the external network while eth1 is connected to the internal network. I would like to setup UFW so that it would allow only traffic from/to specific ports between the external and internal network.

When I enable forwarding the firewall passes traffic regardless of the rules set 

Thanks

---

### Post by boshkash1151 on 2013-11-22
Hi all,
I was able to solve my issue. for others who might face the same problem. 

- In **/etc/default/ufw** set [B]DEFAULT_FORWARD_POLICY="DROP"

[/B]- In **/etc/ufw/before.rules **write the rules to allow traffic flowing from eth0 to eth1 and vice versa. for example to allow port 80

[B]-A ufw-before-forward -i br0 -p tcp  -s a.b.c.d/24 --dport 80 -j ACCEPT
[/B]**-A ufw-before-forward -i br0 -p tcp  -d a.b.c.d/24 --sport 80-j ACCEPT**

where a.b.c.d/24 is your local network and br0 is the bridged interface

---

