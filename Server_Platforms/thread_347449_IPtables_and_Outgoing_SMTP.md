---
title: "IPtables and Outgoing SMTP"
date: 2007-01-27
forum: Server Platforms
---

### Post by galeron on 2007-01-27
Hi,

My router is an Ubuntu router just set up recently. Everything's been going fine, except for one thing. All the computers in my network can receive email, but cannot send. The settings are fine, and I know it's the router that's dropping my packets, because syslog shows that it is blocking SMTP packets.

My "iptables -L" output is as follows:
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/24          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
tcp_packets  tcp  --  anywhere             anywhere            
udp_packets  udp  --  anywhere             anywhere            
icmp_packets  icmp --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT INPUT packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  10.0.0.0/24          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
tcp_packets  tcp  --  anywhere             anywhere            
udp_packets  udp  --  anywhere             anywhere            
icmp_packets  icmp --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT INPUT packet died: ' 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:smtp dpts:1024:65535 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpts:5999:x11 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT FORWARD packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT FORWARD packet died: ' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  localhost            anywhere            
ACCEPT     all  --  10.0.0.2             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT OUTPUT packet died: ' 
bad_tcp_packets  tcp  --  anywhere             anywhere            
ACCEPT     all  --  localhost            anywhere            
ACCEPT     all  --  10.0.0.2             anywhere            
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 3 LOG level debug prefix `IPT OUTPUT packet died: ' 
ACCEPT     tcp  --  10.0.0.0/24          anywhere            tcp spts:1024:65535 dpt:smtp 

Chain allowed (9 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
DROP       tcp  --  anywhere             anywhere            

Chain bad_tcp_packets (6 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            tcp flags:SYN,ACK/SYN,ACK state NEW reject-with tcp-reset 
LOG        tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW LOG level warning prefix `New not syn:' 
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW 
REJECT     tcp  --  anywhere             anywhere            tcp flags:SYN,ACK/SYN,ACK state NEW reject-with tcp-reset 
LOG        tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW LOG level warning prefix `New not syn:' 
DROP       tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW 

Chain icmp_packets (2 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 

Chain tcp_packets (2 references)
target     prot opt source               destination         
allowed    tcp  --  anywhere             anywhere            tcp dpt:ftp 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ssh 
allowed    tcp  --  anywhere             anywhere            tcp dpt:www 
allowed    tcp  --  anywhere             anywhere            tcp dpt:auth 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ftp 
allowed    tcp  --  anywhere             anywhere            tcp dpt:ssh 
allowed    tcp  --  anywhere             anywhere            tcp dpt:www 
allowed    tcp  --  anywhere             anywhere            tcp dpt:auth 
allowed    tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:smtp 

Chain udp_packets (2 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain 

```

Any help is appreciated.

Thanks!

---

### Post by galeron on 2007-01-28
Cant' anyone help?

:cry: :(

---

