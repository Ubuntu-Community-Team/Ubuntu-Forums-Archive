---
title: "opening port"
date: 2008-07-23
forum: Server Platforms
---

### Post by maidei on 2008-07-23
Just install ubuntu sever 8.04.
-how to reverse this command or delete it

iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT ??

i thought I was suppose open port 80 on ubuntu server 8.04, used the above command,
Since I notice that I didnt need to use the command.
Only need to install apache.

So can I reverse this command. If I leave it the way it is, will that be safe

Regards

Maidei




root@maidgal:/home/maidgal2# iptables -v -n -L
Chain INPUT (policy ACCEPT 14108 packets, 678K bytes)
 pkts bytes target     prot opt in     out     source               destination

    8   392 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
        tcp dpt:80
    1    44 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0
        tcp dpt:80

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination


Chain OUTPUT (policy ACCEPT 14017 packets, 595K bytes)
 pkts bytes target     prot opt in     out     source               destination

root@maidgal:/home/maidgal2# sudo iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by BaseRunner on 2008-07-23
Hello,

if you add --line-numbers to your query you get the no.s of all existing rules. You can then use -D <queue> <no> to remove specific rules.
Example:
# iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
# iptables -nL --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         
1    ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

# iptables -D INPUT 1
# iptables -nL --line-numbers
Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination

Cheers
batta

---

