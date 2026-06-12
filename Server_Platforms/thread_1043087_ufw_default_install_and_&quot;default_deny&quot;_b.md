---
title: "ufw default install and &quot;default deny&quot; blocks outgoing as well as incoming"
date: 2009-01-18
forum: Server Platforms
---

### Post by jits on 2009-01-18
Hi,

I'm experiencing some odd behaviour with the current version of ufw (0.16.2.3) - when enabled after install it blocks all outgoing as well as incoming traffic (it should only block incoming).

When I then disable ufw, and then set "default allow" and then enable, it works as expected (both incoming and outgoing allowed), but when I set "default deny" it goes back to blocking ALL traffic.

The iptables rules when this occurs are:

```


Chain INPUT (policy DROP)
target     prot opt source               destination
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-after-forward (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK FORWARD]: '
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-after-input (1 references)
target     prot opt source               destination
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:137
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:138
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:139
RETURN     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:445
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:67
RETURN     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:68
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK INPUT]: '
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-after-output (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-before-forward (1 references)
target     prot opt source               destination
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-before-input (1 references)
target     prot opt source               destination
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-before-output (1 references)
target     prot opt source               destination
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-not-local (0 references)
target     prot opt source               destination

Chain ufw-user-forward (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-user-input (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:22
RETURN     all  --  0.0.0.0/0            0.0.0.0/0

Chain ufw-user-output (1 references)
target     prot opt source               destination
RETURN     all  --  0.0.0.0/0            0.0.0.0/0



```

The last line seems to indicate that outgoing traffic is being blocked, but I don't know enough about iptables and ufw to be certain.

Is this a bug in ufw?

I've verified that no other firewall (or any other software) is loading up rules in iptables apart from ufw (I did disable ufw first and run iptables -L -n).

Any help is greatly appreciated.

Cheers,
Jits

---

