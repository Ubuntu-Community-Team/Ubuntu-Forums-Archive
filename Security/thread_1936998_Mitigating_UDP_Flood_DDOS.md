---
title: "Mitigating UDP Flood DDOS"
date: 2012-03-07
forum: Security
---

### Post by theoneone on 2012-03-07
My box recently has been DOSed, and I accidentaly heard from some ppl that it's Rebel / Shell Booter... How to deny this type of attack?

Ubuntu 10.04, under OpenVZ container. List of modules:

cat /proc/net/ip_tables_matches
> 
udp
tcp
owner
state
length
ttl
tcpmss
multiport
multiport
limit
tos
icmp


It's only running one application, which listens on UDP port 11111 and TCP port 22222...

 > 
## clean all rules and chains
iptables -F
iptables -X

## accepting localhost interface
iptables -A INPUT -i lo -j ACCEPT

## dropping fragmented packets
iptables -A INPUT -f -j DROP

## dropping packet length 0~48 and 2401~65535 as it's not used by the application
iptables -A INPUT -p udp --dport 11111 -m length --length 0:48 -j DROP
iptables -A INPUT -p udp --dport 11111 -m length --length 2401:65535 -j DROP

## syn sanity check
iptables -A INPUT -p tcp ! --syn -m state --state NEW -j DROP

## dropping invalid packet
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A INPUT -p tcp --tcp-flags ALL ALL -j DROP
iptables -A INPUT -p tcp --tcp-flags ALL NONE -j DROP
iptables -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
iptables -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
iptables -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
iptables -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP

## stateful packet inspection
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT

## accepting new 11111 udp connection with a limit of 1/s and burst 8
iptables -A INPUT -p udp --dport 11111 -m state --state NEW -m limit --limit 1/second --limit-burst 8 -j ACCEPT

## accepting new syn connection with a limit of 1/s and burst 3
iptables -A INPUT -p tcp --syn -m limit --limit 1/s --limit-burst 3 -j ACCEPT

## accepting new 22222 tcp connection with a limit of 1/s and burst 3
iptables -A INPUT -p tcp --dport 22222 -m state --state NEW -m limit --limit 1/s --limit-burst 3 -j ACCEPT

## set output chain to behave stateful
iptables -A OUTPUT -p udp --dport 11111 -m state --state NEW -j DROP
iptables -A OUTPUT -p tcp --dport 22222 -m state --state NEW -j DROP
iptables -A OUTPUT -m state --state NEW,ESTABLISHED -j ACCEPT

## set default rules
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
iptables-save


Now my iptables -L -v

> 
**Chain INPUT (policy DROP 127M packets, 57G bytes)**
pkts bytes target prot opt in out source destination
0 0 ACCEPT all -- lo any anywhere anywhere
0 0 DROP all -f any any anywhere anywhere
4039 113K DROP udp -- any any anywhere anywhere udp dpts:11111 length 0:48
2 174 DROP tcp -- any any anywhere anywhere tcp flags:!FIN,SYN,RST,ACK/SYN state NEW
0 0 DROP tcp -- any any anywhere anywhere tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG
2 80 DROP tcp -- any any anywhere anywhere tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE
135K 2M ACCEPT all -- any any anywhere anywhere state ESTABLISHED
28272 1097K ACCEPT icmp -- any any anywhere anywhere icmp echo-request length 0:128 limit: avg 9/sec burst 9
554 30349 ACCEPT udp -- any any anywhere anywhere udp dpt:11111 state NEW limit: avg 1/sec burst 8
255 11160 ACCEPT tcp -- any any anywhere anywhere tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 3
92 3680 ACCEPT tcp -- any any anywhere anywhere tcp dpts:22222 state NEW limit: avg 1/sec burst 3

Chain FORWARD (policy DROP 0 packets, 0 bytes)
pkts bytes target prot opt in out source destination

Chain OUTPUT (policy DROP 29 packets, 2138 bytes)
pkts bytes target prot opt in out source destination
396 25276 DROP udp -- any any anywhere anywhere udp dpts:11111 state NEW
0 0 DROP tcp -- any any anywhere anywhere tcp dpts:22222 state NEW
169K 5M ACCEPT all -- any any anywhere anywhere state NEW,ESTABLISHED



This statistics happened only after 1 hours uptime, then followed by 25 minutes DDOS duration. 57Gbytes packets dropped by firewall, while only around 90Mbytes legitimate packets accepted... But when attack happened, my box still going timeout / down.

Another information, after DDOS happened, I type netstat -tulpn
and it seems that there's around 150.000 Recv-Q in udp port 11111 (usually 0 Recv-Q)

Could anyone of you help me?

Thank you very much, really appreciate it

---

