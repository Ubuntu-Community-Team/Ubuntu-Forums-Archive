---
title: "iptables newbie: anything wrong with allowing all lan traffic?"
date: 2006-09-06
forum: Server Platforms
---

### Post by ?@yk0&amp;^4 on 2006-09-06
Hi everyone. I'm a bit of a newcomer to iptables, I was just wondering whether there's any security problem associated with allowing all local network traffic, as it's easier than configuring each port individually. The internet and local network are on wlan0, all the rules are configured without an interface name. At the moment it's all testing anyway, as I'm behind an NAT firewall...

iptables -L gives:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  10.0.0.0/24          anywhere            
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


Also, do I need to configure anything on the OUTPUT or FORWARD chains? Or can I just leave it to accept all traffic?

Many thanks,
Greg.

---

### Post by Macchi on 2006-09-07
Perhaps you could try some higher level solution for the configuration of iptables. Otherwise it can be more difficult to configure the firewall manually every time you wish to add or modify a service.

Have you tried Firestarter? It is actually only a graphical interface to iptables, thus less suitable for a server without a graphical desktop. Another alternative that seemd interesting is FireHOL. It has a simple and intuitive text-based notation for the configuration file. You can configure it even remotely through ssh and a shell.

Professionally I would never recommend anyone to simply allow all trafic, not even behind a firewall. Several layers increase the level of security. Good security is like an onion and not like a single egg-shell. This is particularly important if you run several services and or have wireless devices connected to your lan.

Sorry by not offering a direct solution but maybe you can use Firestarter or FireHol instead.

---

