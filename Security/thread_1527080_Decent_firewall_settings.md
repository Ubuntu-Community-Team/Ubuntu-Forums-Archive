---
title: "Decent firewall settings"
date: 2010-07-08
forum: Security
---

### Post by fipz on 2010-07-08
Hello everyone,  I know thread's name might sound a bit tricky but i'm looking for some good firewall settings. I tried ufw (former firestarter user so i had to work it out abit lol) and after finishing its configuration iptables -L shows this

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            multiport dports www,https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
DROP       all  --  anywhere             anywhere            

```

UFW status instead

```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-ns 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootps 
ufw-skip-to-policy-input  udp  --  anywhere             anywhere            udp dpt:bootpc 
ufw-skip-to-policy-input  all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-logging-deny  all  --  anywhere             anywhere            state INVALID 
DROP       all  --  anywhere             anywhere            state INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
ufw-logging-deny  all  --  anywhere             anywhere            limit: avg 3/min burst 10 
DROP       all  --  anywhere             anywhere            

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT BLOCK] ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            multiport dports www,https 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
DROP       all  --  anywhere             anywhere            

```is there any odd? does anyone have any hints to make it better ? (im paranoid lol decided to "try to" block almost anything i wont need)


also 

```
Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere 


Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere
```
should that be so?? ACCEPT? isn't that totally against what ufw stated??

thanks in advance

---

### Post by bodhi.zazen on 2010-07-09
IMO the best way to "test" your firewall rules is to scan your box from a second box (nmap).

You also need to define "Decent". Are you on a LAN ? Do you have a router ? Are you running any servers ?

Last, if you wish to examine the rule set use

```
sudo iptables -L -v -n
```You will see those accept rules are for the lo which is appropriate.

For the vast majority of desktop users the defaults are more then adequate, in fact many desktop users probably do not need to activate UFW as they are not running servers.

---

### Post by wacky_sung on 2010-07-09
I still prefer using iptables as my firewall which is so much easy to customize as compare even though i am just an average user who pick it up recently.

---

### Post by fipz on 2010-07-09
thank you (again) bodhi.zazen for your help, i taken some time to reset my firewall, that command shows 

```

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2540 2532K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2540 2532K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy DROP 4 packets, 304 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2257  340K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2257  340K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   304 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   304 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   304 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    4   304 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
    0     0 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   304 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   300 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2510 2510K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
   18 21295 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   18 21295 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
    6   299 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
    6   299 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2540 2532K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2257  340K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   300 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 1990  323K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
  261 16215 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   18 21295 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    6   299 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-reject-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-skip-to-policy-forward (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:143 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:143 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2049 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:2049 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:110 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:110 
    2   128 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 135,139,445 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 137,138 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:22 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:5900 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:5353 
    4   171 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:4662 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:4672 

Chain ufw-user-limit (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 5 LOG flags 0 level 4 prefix `[UFW LIMIT BLOCK] ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

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
  174 10931 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
   83  4980 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           multiport dports 80,443 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:46631 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:46631 

```

 i think this is ok? isn't 0.0.0.0 nothing? (like localhost)


also to answer your question, techs (aka the guys who brought me that, its given by my isp) say its a modem but i think they re fooling me most likely to be a router, not firewalled (sigh lol) and no, no servers at all i even shutdown avahi cups and exim.

To be honest i would have scanned my pc from a second source, but at the moment that second source has windows XP installed and i didn't want to touch it (lol i'll be using that pc again when i can install linux, else no way I need to harden XP even to go on google O_O). nmap online said i had open|filtered ports (worrying lol) grc said i'm stealth.

by the way  thanks again for all your attention

---

### Post by wacky_sung on 2010-07-09
If you like to use iptables firewall.Below is my personal setting without running servers.

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           recent: UPDATE seconds: 86400 name: lastmeasure side: source 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW recent: UPDATE seconds: 60 name: DEFAULT side: source 
    4   200 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
92206  104M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x11/0x01 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x18/0x08 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x30/0x20 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x05/0x05 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x2B 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x37 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x04/0x04 limit: avg 2/sec burst 2 
    5  1209 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 2 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 17 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 13 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 0 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  eth0   *       127.0.0.1            0.0.0.0/0           
    0     0 DROP       all  --  wlan0  *       127.0.0.1            0.0.0.0/0           
    0     0 DROP       udp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 recent: UPDATE seconds: 660 hit_count: 7 name: DEFAULT side: source 
    4  1364 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/24        
    0     0 DROP       all  --  *      *       0.0.0.0/0            127.0.0.0/8         
    0     0 DROP       all  --  *      *       0.0.0.0/0            10.0.0.0/8          
    0     0 DROP       all  --  *      *       0.0.0.0/0            172.16.0.0/12       
    0     0 DROP       all  --  *      *       0.0.0.0/0            192.168.0.0/16      
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/3         

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4   200 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
73505   16M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED 
    0     0 DROP       all  -f  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      eth0    127.0.0.1            0.0.0.0/0           
    0     0 DROP       all  --  *      wlan0   127.0.0.1            0.0.0.0/0           
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:631 
    0     0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:631 
    0     0 DROP       2    --  *      *       0.0.0.0/0            0.0.0.0/0           
```


As below is the setting for my ip6 setting.

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      *      *       ::/0                 ::/0                recent: UPDATE seconds: 86400 name: lastmeasure side: source 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                state NEW recent: UPDATE seconds: 60 name: DEFAULT side: source 
    4   280 ACCEPT     all      lo     *       ::/0                 ::/0                
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 
    0     0 ACCEPT     all      *      *       ::/0                 ::/0                state RELATED,ESTABLISHED 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x17/0x02 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x3F 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x00 
    0     0 ACCEPT     tcp      *      *       ::/0                 ::/0                tcp flags:0x17/0x02 limit: avg 1/sec burst 5 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x11/0x01 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x18/0x08 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x30/0x20 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x05/0x05 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x03/0x03 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x06/0x06 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x3F 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x00 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x29 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x2B 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp flags:0x3F/0x37 
    0     0 ACCEPT     tcp      *      *       ::/0                 ::/0                tcp flags:0x04/0x04 limit: avg 2/sec burst 2 
    0     0 DROP       udp      *      *       ::/0                 ::/0                limit: avg 1/sec burst 2 
    0     0 DROP       all      *      *       ::/0                 ::/0                frag ids:100:200 first 
    0     0 DROP       udp      eth0   *       ::/0                 ::/0                udp dpt:53 recent: UPDATE seconds: 660 hit_count: 7 name: DEFAULT side: source 
    0     0 ACCEPT     icmpv6    *      *       ::/0                 ::/0                ipv6-icmp type 128 limit: avg 30/min burst 5 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 

Chain OUTPUT (policy DROP 6 packets, 384 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    4   280 ACCEPT     all      *      lo      ::/0                 ::/0                
    0     0 DROP       all      *      *       ::/0                 ::/0                state INVALID 
    0     0 ACCEPT     all      *      *       ::/0                 ::/0                state NEW,RELATED,ESTABLISHED 
    0     0 DROP       tcp      *      *       ::/0                 ::/0                tcp dpt:631 
    0     0 DROP       udp      *      *       ::/0                 ::/0                udp dpt:631 
    0     0 DROP       all      *      *       ::/0                 ::/0                frag ids:100:200 first 

```

---

