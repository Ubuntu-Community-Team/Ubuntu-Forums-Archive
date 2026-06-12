---
title: "iptables problem"
date: 2009-02-18
forum: Security
---

### Post by Sporkman on 2009-02-18
For some reason, iptables is not accepting this rule:

```
/lib/iptables> sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables: No chain/target/match by that name

```

Note that I have ubuntu 8.04 server running in a virtualized machine (at a hosting company). Iptables version is v1.3.8.

This is a newly setup virtual dedicated server, and I've never had any problems with the above rule. (It doesn't like "sudo iptables -A INPUT -m state --state INVALID -j DROP" either...)

---

### Post by HermanAB on 2009-02-19
What does iptables -L show?

Cheers,

Herman

---

### Post by Sporkman on 2009-02-19
> **HermanAB said:**
> What does iptables -L show?

Cheers,

Herman

```

/var/log> sudo iptables -L -v
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
   33  2702 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:www limit: avg 400/sec burst 800 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:424 limit: avg 400/sec burst 800 
 1947  150K ACCEPT     all  --  any    any     <my home IP address> anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:<secret ssh port> limit: avg 4/min burst 5 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:<secret ssh port> limit: avg 4/min burst 5 
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:9004 limit: avg 6/min burst 5 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            udp dpt:9004 limit: avg 6/min burst 5 
   23  2004 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 1/sec burst 5 
 1634  224K DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2591 packets, 327K bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

(...and, on a similar strange note, my /var/log/auth.log is completely empty... Is this just virtual container oddness that I'll have to get used to?)

---

### Post by HermanAB on 2009-02-19
Gottit - you have to add a target interface to that rule.

See man iptables.

Cheers,

Herman

---

### Post by Sporkman on 2009-02-19
> **HermanAB said:**
> Gottit - you have to add a target interface to that rule.

See man iptables.


You mean with "-i"? But the manpage says: "If this option is omitted, any interface name will match."...

---

### Post by HermanAB on 2009-02-19
The omission only works if your system has only one interface.  When you use a virtualizer, you end up with many interfaces, so you got to specify which one to use.

Cheers,

Herman

---

### Post by Sporkman on 2009-02-19
No luck:

```
/home> sudo iptables -A INPUT -i venet0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables: No chain/target/match by that name

```

---

### Post by HermanAB on 2009-02-19
The port exists?
$ /sbin/ifconfig venet0

Cheers,

H

---

### Post by Sporkman on 2009-02-19
> **HermanAB said:**
> The port exists?
$ /sbin/ifconfig venet0


Yes, I think it's legit..? :

> /home/sporkforge/text/slush_8Y5stI> /sbin/ifconfig venet0
venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:127.0.0.1  P-t-P:127.0.0.1  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:110865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122945857 (117.2 MB)  TX bytes:5684846 (5.4 MB)



---

### Post by HermanAB on 2009-02-19
Clueless... sorry!

H.

---

### Post by Sporkman on 2009-02-19
> **HermanAB said:**
> Clueless... sorry!

H.

No problem, thanks for trying!

---

### Post by koenn on 2009-02-20
> **Sporkman said:**
> 
```
/lib/iptables> sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables: No chain/target/match by that name

```
(It doesn't like "sudo iptables -A INPUT -m state --state INVALID -j DROP" either...)
It complains about  'No chain/target/match by that name' and I gather from your post that when you change the chain and the target (OUTPUT, DROP), it still doesn't work, so it seems to have a problem with the match 'state'.

iptables / netfilter is modular, so this seems to suggest the module that handles 'matching state' isn't there.

Have a look in /lib/modules/$(uname -r)/kernel/net/ipv4/netfilter
if there is NO  xt_state.ko file there, that's most likely your problem. 
(but if the file is there, that doesn't rule out that there is a problem with the state module)

---

