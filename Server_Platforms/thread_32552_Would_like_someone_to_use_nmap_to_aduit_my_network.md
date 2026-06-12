---
title: "Would like someone to use nmap to aduit my network"
date: 2005-05-08
forum: Server Platforms
---

### Post by DaturaX on 2005-05-08
Hey guys,

Just configured IPtables on my linux firewall. Will like someone to do an audit on my firewall. 

Will PM you my IP address and you can post the findings here and we can discuss on it.

Thanks!

---

### Post by LordHunter317 on 2005-05-08
While an nmap scan is a good idea, posting your IPtables ruleset without your public address is a good idea so it can be audited.

---

### Post by DaturaX on 2005-05-08
[QUOTE=LordHunter317]While an nmap scan is a good idea, posting your IPtables ruleset without your public address is a good idea so it can be audited.[/QUOTE]

```
~ # iptables -v -L
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  992  125K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 DROP       udp  --  vlan1  any     anywhere             anywhere            udp dpt:route
    0     0 DROP       udp  --  br0    any     anywhere             anywhere            udp dpt:route
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:route
    0     0 logdrop    icmp --  vlan1  any     anywhere             anywhere
    8   232 ACCEPT     igmp --  any    any     anywhere             anywhere
    1    72 ACCEPT     all  --  lo     any     anywhere             anywhere            state NEW
   13  1435 logaccept  all  --  br0    any     anywhere             anywhere            state NEW
    2   656 logdrop    all  --  any    any     anywhere             anywhere

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
    7  1178 ACCEPT     all  --  br0    br0     anywhere             anywhere
    0     0 logdrop    all  --  any    any     anywhere             anywhere            state INVALID
    0     0 TCPMSS     tcp  --  any    any     anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1461:65535 TCPMSS set 1460
 3581  349K lan2wan    all  --  br0    any     anywhere             anywhere
 6917 3566K ACCEPT     all  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED
    0     0 logaccept  udp  --  vlan1  any     anywhere             BASE-ADDRESS.MCAST.NET/4 udp
    1    51 logaccept  udp  --  any    any     anywhere             heng-pc             udp dpt:6346
    0     0 logaccept  tcp  --  any    any     anywhere             heng-pc             tcp dpt:6346
    0     0 logaccept  tcp  --  any    any     anywhere             dave                tcp dpt:1659
   33  1608 logaccept  tcp  --  any    any     anywhere             dave                tcp dpt:6881
    0     0 logaccept  udp  --  any    any     anywhere             dave                udp dpt:6881
    0     0 logaccept  tcp  --  any    any     anywhere             dave-2003server     tcp dpt:webcache
    0     0 logaccept  udp  --  any    any     anywhere             dave                udp dpt:113
    9  3913 logaccept  tcp  --  any    any     anywhere             dave                tcp dpts:1024:5000
    0     0 logaccept  udp  --  any    any     anywhere             dave                udp dpts:1024:5000
    0     0 logaccept  tcp  --  any    any     anywhere             dave                tcp dpt:ircd
    0     0 logaccept  udp  --  any    any     anywhere             dave                udp dpt:ircd
    0     0 logaccept  tcp  --  any    any     anywhere             dave-2003server     tcp dpt:ftp
    0     0 logaccept  tcp  --  any    any     anywhere             dave                tcp dpts:5000:5001
    0     0 logaccept  tcp  --  any    any     anywhere             dave-2003server     tcp dpt:ssh
    0     0 logaccept  udp  --  any    any     anywhere             dave-2003server     udp dpt:ssh
    0     0 logaccept  tcp  --  any    any     anywhere             dave-2003server     tcp dpt:www
    0     0 logaccept  udp  --  any    any     anywhere             dave-2003server     udp dpt:www
    0     0 logaccept  tcp  --  any    any     anywhere             dave-2003server     tcp dpt:10000
    0     0 logaccept  udp  --  any    any     anywhere             dave-2003server     udp dpt:10000
    0     0 TRIGGER    all  --  vlan1  br0     anywhere             anywhere            TRIGGER type:in match:0 relate:0
  457 22948 trigger_out  all  --  br0    any     anywhere             anywhere
  457 22948 logaccept  all  --  br0    any     anywhere             anywhere            state NEW
    0     0 logdrop    all  --  any    any     anywhere             anywhere

Chain OUTPUT (policy ACCEPT 1056 packets, 121K bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_1 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_10 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_2 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_3 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_4 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_5 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_6 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_7 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_8 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain advgrp_9 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_1 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_10 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_2 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_3 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_4 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_5 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_6 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_7 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_8 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain grp_9 (0 references)
 pkts bytes target     prot opt in     out     source               destination

Chain lan2wan (1 references)
 pkts bytes target     prot opt in     out     source               destination

Chain logaccept (22 references)
 pkts bytes target     prot opt in     out     source               destination
  513 29955 ACCEPT     all  --  any    any     anywhere             anywhere

Chain logdrop (4 references)
 pkts bytes target     prot opt in     out     source               destination
    2   656 LOG        all  --  any    any     anywhere             anywhere            state NEW LOG level warning tcp-sequence tcp-options ip-options prefix `DROP '
    0     0 LOG        all  --  any    any     anywhere             anywhere            state INVALID LOG level warning tcp-sequence tcp-options ip-options prefix `DROP '
    2   656 DROP       all  --  any    any     anywhere             anywhere

Chain logreject (0 references)
 pkts bytes target     prot opt in     out     source               destination
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `WEBDROP '
    0     0 REJECT     tcp  --  any    any     anywhere             anywhere            tcp reject-with tcp-reset

Chain trigger_out (1 references)
 pkts bytes target     prot opt in     out     source               destination

```

I opened port 1024 to 5000 for IRC dcc send. Anyone knows of a more secure way to go about dcc send other than port triggering?

---

### Post by LordHunter317 on 2005-05-08
*sigh* That's the messy sevasoft crap, isn't?

Anyway, without know what interfaces go to what parts of your network, it's a touch hard for anyone to audit it.

---

