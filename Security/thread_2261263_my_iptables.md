---
title: "my iptables"
date: 2015-01-17
forum: Security
---

### Post by ant2ne on 2015-01-17
someone please tell me how come I can ssh in from 10.1.2.113?
```
[root@server sysconfig]# cat iptables
# Firewall configuration written by system-config-firewall
# Manual customization of this file is not recommended.
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
-A INPUT -p icmp -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 22 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 137 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 138 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 139 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 445 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.1.0/24 -m tcp -p tcp --dport 631 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.2.0/24 -m tcp -p tcp --dport 137 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.2.0/24 -m tcp -p tcp --dport 138 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.2.0/24 -m tcp -p tcp --dport 139 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.2.0/24 -m tcp -p tcp --dport 445 -j ACCEPT
-A INPUT -m state --state NEW -s 10.1.2.0/24 -m tcp -p tcp --dport 631 -j ACCEPT

-I INPUT -m state --state NEW -s 10.1.1.69 -p tcp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-I INPUT -m state --state NEW -s 10.1.2.25 -p tcp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-I INPUT -m state --state NEW -s 10.1.2.24 -p tcp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-I INPUT -m state --state NEW -s 10.1.1.69 -p udp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-I INPUT -m state --state NEW -s 10.1.2.25 -p udp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-I INPUT -m state --state NEW -s 10.1.2.24 -p udp  -m multiport --dport 111,892,2049,32803,39165,32769 -j ACCEPT
-A INPUT -j DROP
-A FORWARD -j DROP
COMMIT

```





```
[root@server sysconfig]# iptables -L -n -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     udp  --  *      *       10.1.2.24            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
    0     0 ACCEPT     udp  --  *      *       10.1.2.25            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
    0     0 ACCEPT     udp  --  *      *       10.1.1.69            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.24            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.25            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
    0     0 ACCEPT     tcp  --  *      *       10.1.1.69            0.0.0.0/0           state NEW multiport dports 111,892,2049,32803,39165,32769 
  214 17132 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:137 
    0     0 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:138 
    0     0 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:139 
    1   130 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:445 
    0     0 ACCEPT     tcp  --  *      *       10.1.1.0/24          0.0.0.0/0           state NEW tcp dpt:631 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.0/24          0.0.0.0/0           state NEW tcp dpt:137 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.0/24          0.0.0.0/0           state NEW tcp dpt:138 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.0/24          0.0.0.0/0           state NEW tcp dpt:139 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.0/24          0.0.0.0/0           state NEW tcp dpt:445 
    0     0 ACCEPT     tcp  --  *      *       10.1.2.0/24          0.0.0.0/0           state NEW tcp dpt:631 
   38  3505 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 170 packets, 33056 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by The Cog on 2015-01-17
It doesn't look like you should be able to accept new TCP connections from 10.1.2.113. Any connection established before the rules are applied can continue though.
Rules in the mangle table might be intercepting something.

What makes you think that you can ssh in from 10.1.2.113?
Can you post the output from "iptables-save -c" which lists all tables and entries along with packet and byte counts.

---

### Post by ant2ne on 2015-01-17
Yeah, IDK it is working correctly now. I swear I restarted iptables and logged out and in several times. Another one of those flukes. I don't suppose you can tellm me why my nfs sessions from 10.1.2.24 cant reach this server?

---

### Post by Doug S on 2015-01-18
> **ant2ne said:**
> I don't suppose you can tellm me why my nfs sessions from 10.1.2.24 cant reach this server?No We can't, because as I understand it, from what little reading I did, the high numbered ports used are decided by your nfs configuration files.

---

