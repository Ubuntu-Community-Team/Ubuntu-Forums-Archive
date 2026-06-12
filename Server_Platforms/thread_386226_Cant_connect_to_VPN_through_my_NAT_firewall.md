---
title: "Cant connect to VPN through my NAT firewall"
date: 2007-03-16
forum: Server Platforms
---

### Post by jboss1995 on 2007-03-16
I'm trying to connect to my poptop VPN on the internet. I had it working for a time but just stopped. I replaced a freebsd server NAT firewall server with a ubuntu NAT firewall. Like I said it worked for a time until I setup a poptop server on it as well (it works fine) but i can't connect to VPNs on the outside. Here is my iptables

ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp flags:ACK/ACK 
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            state RELATED 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain dpts:1024:65535 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:smtp 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:auth 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:https 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:1723  
ACCEPT     gre  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
DROP       tcp  --  anywhere             anywhere            tcp dpts:nfs:2050 
DROP       tcp  --  anywhere             anywhere            tcp dpts:x11:6063 
DROP       tcp  --  anywhere             anywhere            tcp dpts:afs3-fileserver:7010 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  10.0.0.0/24          anywhere            
ACCEPT     all  --  anywhere             10.0.0.0/24         state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


I was hoping there was a way I could turn no some kind of logging and see what is going on. I'm sure it has something to do with gre (47) but as you can see it is set to ACCEPT:mad: 

Thanks for your help in advance

---

