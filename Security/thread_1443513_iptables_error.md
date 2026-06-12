---
title: "iptables error"
date: 2010-03-31
forum: Security
---

### Post by savin on 2010-03-31
please help me..
thanks in advance....

chain INPUT (policy DROP)
target     prot opt source         destination         
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:ssh 
ACCEPT     tcp  --  anywhere       arl-sandbox         tcp dpt:1050 
ACCEPT     all  --  anywhere       anywhere            
ACCEPT     all  --  anywhere       anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:http-alt 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:https 
ACCEPT     udp  --  anywhere       anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere       anywhere            tcp dpt:domain 
ACCEPT     icmp --  anywhere       anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 




Error under following conditions :

target    prot  opt   source                 destination 	      port

1.ACCEPT  tcp   --    192.168.2.X     arl-sandbox(204.232.200.X)   tcp dpt:1050 

2.#( by removing tis line) 
ACCEPT    tcp   --     anywhere           anywhere            tcp dpt:1050


By Default its
Doing 2. and not doin 1.      eventhough with following rules

1. DROP   tcp  --     192.168.2.X      204.232.200.X         tcp dpt:1050
2. ACCEPT tcp    --      anywhere           anywhere         tcp dpt:1050


if removing  2.     by default its blocking every connection to 1050
though allowing 

ACCEPT  tcp    --     192.168.2.X       204.232.200.X         tcp dpt:1050

---

