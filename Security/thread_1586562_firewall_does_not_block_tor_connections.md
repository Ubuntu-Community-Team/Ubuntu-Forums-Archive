---
title: "firewall does not block tor connections"
date: 2010-10-02
forum: Security
---

### Post by eskaemma on 2010-10-02
Hello for the first time.  I have noticed interesting problem. I use two browsers - Firefox and Konqueror. Konqueror is configured to use tor, Firefox not. Using Gufw I block all incoming and outgoing traffic and it works while using Firefox, I mean that I can't view any www site and it is ok. But if I use Konqueror I can establish any conection. How to understand this? Should I have different firewall while using tor? Have you any suggestions?

---

### Post by bodhi.zazen on 2010-10-02
Hard to know from what you posted. 

How did you configure your firewall ?

---

### Post by Aetixintro on 2010-10-02
You can try to use the Firestarter that I think is splendid! Just use its Lockdown option which seems to be want you want.

You can experiment from there with all the various options. You [SIZE=3]should[SIZE=2] check out Firestarter. It's hugely underrated, IMO.

Good luck with your Ubuntu and the browsing! :)
[/SIZE][/SIZE]

---

### Post by eskaemma on 2010-10-03
I think I have solved this problem. Let me explain:

1. tor is running. I check it by netstat -apntu and it shows:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      1433/polipo     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1560/cupsd      
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1417/exim4      
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      1523/tor        
tcp        0      0 172.25.22.30:53532      81.2.197.33:80          ESTABLISHED 1523/tor        
tcp        0      0 172.25.22.30:58356      173.193.219.190:443     ESTABLISHED 1523/tor        
tcp        0      0 172.25.22.30:60097      174.36.199.201:443      ESTABLISHED 1523/tor        
tcp        0      0 172.25.22.30:49115      91.208.34.14:443        ESTABLISHED 1523/tor        
udp        0      0 0.0.0.0:68              0.0.0.0:*                           997/dhclient    

```

2. At the same time Firewall works without blocking too much. iptables -L -v -n shows:

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2586 1594K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2586 1594K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   51  5228 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
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

Chain OUTPUT (policy DROP 52 packets, 3184 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2390  380K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2390  380K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   52  3184 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   52  3184 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   52  3184 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   52  3184 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

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
   51  5228 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   52  3184 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  138 54930 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2397 1534K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
   51  5228 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
   51  5228 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2586 1594K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2390  380K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  138 54930 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 1126  251K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 1126 74178 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
   51  5228 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
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
   51  5228 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

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

Chain ufw-user-logging-output (10 references)
 pkts bytes target     prot opt in     out     source               destination         
   11   660 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
   17  1020 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
   21  1260 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
   34  2040 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
   26  1729 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
 1012 67274 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
   11   660 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
   11   660 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:21 limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 
    0     0 RETURN     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:21 

Chain ufw-user-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   17  1020 ufw-user-logging-output  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
   17  1020 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80 
    0     0 ufw-user-logging-output  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:80 
   34  2040 ufw-user-logging-output  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
   34  2040 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443 
    0     0 ufw-user-logging-output  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:443 
    0     0 ufw-user-logging-output  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
 1012 67274 ufw-user-logging-output  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
 1012 67274 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:53 
   11   660 ufw-user-logging-output  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43 
   11   660 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:43 
    0     0 ufw-user-logging-output  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:43 
    0     0 ufw-user-logging-output  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:21 
    0     0 ufw-user-logging-output  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:21 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:21 


```

3. And now I set firewall to block everything. iptables -L -v -n shows:

```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2805 1624K ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2805 1624K ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
   70  7179 ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
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

Chain OUTPUT (policy DROP 176 packets, 11384 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 2714  402K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 2714  402K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  176 11384 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  176 11384 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  176 11384 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  176 11384 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

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
   70  7179 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  176 11384 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  138 54930 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
 2597 1562K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
   70  7179 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
   70  7179 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2805 1624K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 2714  402K LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW AUDIT] ' 

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
  138 54930 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
 1136  252K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
 1440 94912 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
   70  7179 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
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
   70  7179 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

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


```

4. But tor is still working.

5. By commands: service tor stop, and service polipo stop I stop tor.

6. Now I start these services (remember that now firewall is blocking everything).

7. Command netstat -apntu shows:

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN      3689/polipo     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1560/cupsd      
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      3679/tor        
tcp        0      1 172.25.22.30:49783      174.36.199.201:443      SYN_SENT    3679/tor        
tcp        0      1 172.25.22.30:34623      91.208.34.26:443        SYN_SENT    3679/tor        
tcp        0      1 172.25.22.30:46135      81.2.197.33:80          SYN_SENT    3679/tor        
tcp        0      1 172.25.22.30:56016      173.193.219.190:443     SYN_SENT    3679/tor        
tcp        0      1 172.25.22.30:42008      94.23.158.26:9001       SYN_SENT    3679/tor        
udp        0      0 0.0.0.0:68              0.0.0.0:*                           997/dhclient    

```

8. And I think that problem is solved.

9. I can't use Firestarter because it doesn't support ipv6 by default. Now I have ipv6 disabled in my system, but if I would like to use it ufw will be better I think.

Thank you for interesting  this problem.

---

### Post by bodhi.zazen on 2010-10-03
I can no tell from your post what exactly you are concerned with.

When you use ufw to block inbound connections, it blocks NEW connections.

RELATED and ESTABLISHED connections are allowed.

Thus Tor is expected to work with your firewall enabled.

If you do not understand all that about NEW, RELATED, and ESTABLISHED connections, read the first part of this page :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by eskaemma on 2010-10-03
I think that ESTABLISHED and RELATED is a key to understand this. I must read a little bit more about it.
Thank you very much for your advice.

---

