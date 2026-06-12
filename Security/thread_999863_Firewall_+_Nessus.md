---
title: "Firewall + Nessus"
date: 2008-12-02
forum: Security
---

### Post by Sarmacid on 2008-12-02
I set up Nessus on Ubuntu server 8.04, and if anyone could help me set up the firewall, I'd really appreciate it. So far, I'm allowing all connections going out with the stablished and new flags. Incoming, I'm allowing all connections that have been stablished, http connections that are new or stablished(Since I need many people to view the reports), DNS(UDP only), NTP and RADIUS.

I was wondering if I should allow all incoming UDP packages, but I don't know if Nessus actually needs those. Here are the rules I've got so far

**The Ubuntu server is:**        192.168.1.1
**I am:**                        192.168.1.2(I manage the server from here)
**Other servers: **              192.168.1.3

```
# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             192.162.1.1      state ESTABLISHED
ACCEPT     tcp  --  anywhere             192.162.1.1      tcp dpt:www state NEW,ESTABLISHED
ACCEPT     tcp  --  192.162.1.2		 192.162.1.1      tcp dpt:ssh state NEW,ESTABLISHED
ACCEPT     tcp  --  192.162.1.2  	 192.162.1.1      tcp dpt:webmin state NEW,ESTABLISHED
ACCEPT     udp  --  192.162.1.3		 192.162.1.1      udp spt:domain
ACCEPT     udp  --  192.162.1.3		 192.162.1.1      udp spt:domain
ACCEPT     udp  --  192.162.1.3		 192.162.1.1      udp spt:ntp
ACCEPT     udp  --  192.162.1.3		 192.162.1.1      udp spt:radius
ACCEPT     udp  --  192.162.1.3		 192.162.1.1      udp spt:radius-acct

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
ACCEPT     all  --  192.162.1.1       	 anywhere            state NEW,ESTABLISHED
```

The first lines in INPUT and OUTPUT saying anywhere/anywhere are from the loopback interface.

---

