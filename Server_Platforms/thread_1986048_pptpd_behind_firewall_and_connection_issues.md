---
title: "pptpd behind firewall and connection issues"
date: 2012-05-24
forum: Server Platforms
---

### Post by karaluh on 2012-05-24
I'm trying to set up pptpd server. It's virtualized and works, when connecting from LAN. When I'm trying to connect from the outside using the same Win XP laptop, I get error 649, no syslog messages on pptpd server. The firewall is also Ubuntu, all policies are ACCEPT, ports are forwarded:
```
Chain PREROUTING (policy ACCEPT)
target  prot opt source            destination  
[...]
DNAT    gre  --  anywhere          anywhere         to:192.168.0.12 
DNAT    tcp  --  anywhere          anywhere         tcp dpt:1723 to:192.168.0.12
[...]
```
modules are inserted:
```
Module                  Size  Used by
nf_nat_pptp             3712  0 
nf_nat_proto_gre        2820  1 nf_nat_pptp
nf_conntrack_pptp       7040  1 nf_nat_pptp
nf_conntrack_proto_gre     5632  1 nf_conntrack_pptp
[...]
```
What am I missing?

---

