---
title: "IP forwarding help"
date: 2005-10-18
forum: Server Platforms
---

### Post by elasticwings on 2005-10-18
Hi, I'm having trouble getting https to forward to the mail server I am firewalling.  Here is what my iptables looks like.  And I did the thing in sysctl.conf for net.ipv4.ip_forward = 1 plus I echoed it into the /proc location to apply it immediately and restarted the network.  Is there something else I am missing?


```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:pop3s
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  10.1.0.0/16          anywhere
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED
ACCEPT     tcp  --  anywhere             exchange.blah.com    tcp dpt:pop3
ACCEPT     tcp  --  anywhere             exchange.blah.com    tcp dpt:https
ACCEPT     tcp  --  anywhere             exchange.blah.com    tcp dpt:imaps
ACCEPT     tcp  --  anywhere             exchange.blah.com    tcp dpt:pop3s

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by elasticwings on 2005-10-18
Bizzump

---

