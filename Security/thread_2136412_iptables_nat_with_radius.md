---
title: "iptables nat with radius"
date: 2013-04-17
forum: Security
---

### Post by Leo Matheus on 2013-04-17
i have a free-radius server that authenticate some nodes on my network. Between the server and the nodes there is a firewall iptables.

the free-radius is on a external network, and the nodes are on the internal network.

im using the following rules on the firewall for nat:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
iptables -t nat -A PREROUTING -i eth0 -j DNAT --to 192.168.YY.yy
iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.XX.xx

where 192.168.YY.yy is the internal adress and 192.168.XX.xx is the external adress.

tand this is the radius rules:

iptables -t mangle -A PREROUTING -d 192.168.XX.xx -p tcp --dport 1813 -j MARK --set-mark 1 -i eth0
iptables -t nat -A PREROUTING -p tcp -m mark --mark 1 -j DNAT --to-destination 192.168.YY.zz -i eth0
iptables -t nat -A POSTROUTING -m mark  --mark 1 -j SNAT --to-source 192.168.YY.yy -o eth1
iptables -A FORWARD -m mark --mark 1 -j ACCEPT -o eth1

192.168.YY.zz is the ip of a node.

my problem is that is: the radius rules just can be made for just one node, and i have at last 4 of then.
i can't create 4 times this rules for that, because it will send for all the nodes. there is any way to make this without send to all?

---

