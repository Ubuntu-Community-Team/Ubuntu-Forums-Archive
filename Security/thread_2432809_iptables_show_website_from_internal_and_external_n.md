---
title: "iptables show website from internal and external network"
date: 2019-12-09
forum: Security
---

### Post by sarto76 on 2019-12-09
Hi,
I have an iptables server with 3 interfaces (ens33 -->external, internet, ens38 -->internal, private, ens39-->DMZ)
In the ens39 I have a webserver and I want it to be accessible from external and internal network.
From external is ok:
iptables -t nat -A POSTROUTING -o ens33  -j MASQUERADE
iptables -A FORWARD -i ens39 -o ens33 -j ACCEPT  (so I can also update my webserver)
iptables -A FORWARD -i ens33 -o ens39 -j ACCEPT
iptables -A PREROUTING -i ens33 -p tcp --dport 80 -j DNAT --to 192.168.198.2:80

How can I access the webserver from the ens38 network (192.168.238.0/24)?
if I put a PREROUTING rule than I can access to the webserver from the private network but I cannot go to internet anymore...
Thank you Max

---

### Post by lensman3 on 2019-12-10
I believe you will need the "route" command.  The "route" command informs the IP stack which ether card to send packs out and to which IP address to accept packets. It is fairly easy to route the two internal cards so packets can get to the Internet, but it is harder to forward packets from one internal card to the other and back again.  Iptables does not route packets and the "iptables forward" only checks if those packets can be forwarded.

I would delete the firewall until you get the 'route' commands working.

New versions of Linux want you to use the 'ip route' commands.  IPv4 and IPv6 protocols will need there on "route" entries.

---

