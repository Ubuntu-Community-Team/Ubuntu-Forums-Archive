---
title: "Firewalling for clients using Openvpn"
date: 2016-07-30
forum: Security
---

### Post by marwanq on 2016-07-30
Hey all..

i have been trying to enforce firewall policies for openvpn clients but so far i am not able to achieve anything
This is how all my set up looks like:

my open vpn server is 10.8.0.1 while my client is 10.8.0.6  and i am routing the client's traffic through openvpn server(i followed this [https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html) ).

Both of them are fully functional and if i do traceroute for some website on the client so the first ip it shows is of the vpn server that is 10.8.0.1.
it forwards the traffic from tun0 to eth0 and invovles a bit of masquerading.

Now what i am trying to achieve is to block let say A.B.C.D on client but i want all these rules to be enforced on the openvpn server rather than the client.
so far i have tired these commands but they dont seem to help:
1) sudo ufw deny from 10.8.0.6 to A.B.C.D
2)sudo ufw deny from 10.8.0.1 to A.B.C.D
3)sudo ufw deny out on tun0 to A.B.C.D
4)sudo ufw deny from X.X.X.X( eth0's ip )  to A.B.C.D  (it blocks ip on the openvpn server but not on the client)

Please help me on this..

thanks.

---

### Post by kyrithis on 2016-07-30
Your explanation is a bit confusing, I apologize. You'd like to restrict a client from accessing a specific IP in OpenVPN?

---

### Post by SeijiSensei on 2016-07-30
We can only analyze firewalling rules in their full context.  The order of rules is important, and it's possible there is some rule higher up the chain that is interfering with your efforts.  AFAIK, ufw is just a front-end for iptables, so might you post the contents of "sudo iptables -L -nv" inside of [noparse]```

```[/noparse] tags?

---

### Post by marwanq on 2016-07-30
> **kyrithis said:**
> Your explanation is a bit confusing, I apologize. You'd like to restrict a client from accessing a specific IP in OpenVPN?



yup this is what i am trying to do. i am forwarding all my client's traffic through the openvpn server and i want all sort of restrictions to be applied at the server itself.

---

### Post by marwanq on 2016-07-30
> **SeijiSensei said:**
> We can only analyze firewalling rules in their full context.  The order of rules is important, and it's possible there is some rule higher up the chain that is interfering with your efforts.  AFAIK, ufw is just a front-end for iptables, so might you post the contents of "sudo iptables -L -nv" inside of [noparse]```

```[/noparse] tags?


```

Chain INPUT (policy DROP 7 packets, 240 bytes)
 pkts bytes target     prot opt in     out     source               destination         
19796   16M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
19796   16M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  110  9509 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   28  1108 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   28  1108 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   28  1108 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 5239 3300K ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 5239 3300K ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  181 10860 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  181 10860 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  181 10860 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  181 10860 ufw-track-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 1 packets, 84 bytes)
 pkts bytes target     prot opt in     out     source               destination         
18876 4806K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
18876 4806K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1233 84774 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1233 84774 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1233 84774 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1233 84774 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   71  5826 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:137
    9  2175 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:138
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:139
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:445
    1   329 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:67
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:68
    1    71 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  181 10860 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   28  1108 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1233 84774 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 5058 3289K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
  181 10860 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1520  144K ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
18056   16M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 3
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 4
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 11
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 12
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
  220 27736 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  107 18101 ACCEPT     udp  --  *      *       0.0.0.0/0            224.0.0.251          udp dpt:5353
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            239.255.255.250      udp dpt:1900
  113  9635 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   60  4799 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW AUDIT] "

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   87 23585 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW AUDIT] "

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   87  7149 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW AUDIT] "

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 1520  144K ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
16123 4577K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
 1233 84774 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate INVALID LOG flags 0 level 4 prefix "[UFW AUDIT INVALID] "
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    5   346 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
  133 18989 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
   82  8401 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
   82  8401 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   70  4200 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
  111  6660 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  384 23040 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW
  807 58344 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:22
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:22
    3   126 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:1194
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:8000
    0     0 DROP       tcp  --  *      *       10.8.0.6             0.0.0.0/0            tcp dpt:443
    0     0 DROP       udp  --  *      *       10.8.0.6             0.0.0.0/0            udp dpt:443
    0     0 DROP       all  --  *      *       10.8.0.6             216.58.211.99       

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-input (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-logging-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            216.58.211.195      
    0     0 DROP       all  --  *      *       0.0.0.0/0            1.1.1.1             
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.13        
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.2         
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.21        
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.1.254       





```

---

