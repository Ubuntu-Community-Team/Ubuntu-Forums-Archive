---
title: "Empathy and iptables"
date: 2010-06-10
forum: Security
---

### Post by mnoga on 2010-06-10
Hello,

I have recently installed the 10.04v and I configured iptables with FWbuilder. I have configured 5 rules:

- Anti spoofing rule
- All allowed through loopback
- From any to firewall ping reply allowed
- From firewall to any domain, http, https, imaps, smtps allowed
- All denied

I have tested the configuration and its OK. But when I open Empathy I can connect to MSN Messenger service, which uses 1863 port, that is in theory closed. Anyone knows why??

There is my iptables configuration:
> 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 0 code 0 state NEW 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state NEW 
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 state NEW 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports www,https,imaps,ssmtp state NEW 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain state NEW 
RULE_4     all  --  anywhere             anywhere            state NEW 

Chain Cid2690X2345.0 (0 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            icmp type 8 code 0 
ACCEPT     tcp  --  anywhere             anywhere            tcp multiport dports www,https,imaps,ssmtp 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 

Chain In_RULE_0 (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `RULE 0 -- DENY ' 
DROP       all  --  anywhere             anywhere            

Chain RULE_4 (3 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level info prefix `RULE 4 -- DENY ' 
DROP       all  --  anywhere             anywhere  Thanks!

---

### Post by mechdave on 2010-06-10
My memory of iptables is a little rusty but from memory aren't you meant to log/drop,(deny I wouldn't use as it sends feedback to the source what is happening, drop just drops the packet thus if someone is probing your firewall they get no response as if nothing is there), everything and then allow certain ports/protocols from there?

---

