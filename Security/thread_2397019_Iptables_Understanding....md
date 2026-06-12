---
title: "Iptables Understanding..."
date: 2018-07-24
forum: Security
---

### Post by stewartrose2 on 2018-07-24
Good Afternoon Team,

  I need some understanding of this line of code and what rules need to be created to allow access please...

Jul 24 12:57:07 phoenix kernel: Firewall: *UDP_OUT Blocked* IN= OUT=eth0 SRC=x.x.x.x DST=y.y.y.y LEN=55 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55555 DPT=62010 LEN=35 UID=0 GID=0

Thanks in advanced....from Alan

---

### Post by Doug S on 2018-07-24
We need some more information. What would help is if you could give us your entire iptables rule set. For example from:
```
sudo iptables -v -x -n -L
```and if applicable:```
sudo iptables -t nat -v -x -n -L
```

---

### Post by stewartrose2 on 2018-07-25
Thank you for the information, here is the read out below
Flush Iptables

Iptables Tables reloaded
```
[root@phoenix-f ~]# iptables -v -x -n -L
Chain INPUT (policy DROP 2 packets, 72 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  !lo    *       8.8.4.4              0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  !lo    *       8.8.4.4              0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  !lo    *       8.8.4.4              0.0.0.0/0           tcp spt:53 
       0        0 ACCEPT     udp  --  !lo    *       8.8.4.4              0.0.0.0/0           udp spt:53 
       0        0 ACCEPT     tcp  --  !lo    *       8.8.8.8              0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  !lo    *       8.8.8.8              0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  !lo    *       8.8.8.8              0.0.0.0/0           tcp spt:53 
       0        0 ACCEPT     udp  --  !lo    *       8.8.8.8              0.0.0.0/0           udp spt:53 
     610    58169 LOCALINPUT  all  --  !lo    *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
     328    44653 INVALID    tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  !lo    *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 
       0        0 LOGDROPIN  icmp --  !lo    *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
       0        0 ACCEPT     icmp --  !lo    *       0.0.0.0/0            0.0.0.0/0           
     597    57433 ACCEPT     all  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:20 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:21 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:25 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:53 
       2      104 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:80 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:110 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:143 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:443 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:465 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:587 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:993 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:995 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2200 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2030 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2031 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2082 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2083 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2086 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2087 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2095 
       4      240 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:3306 
       0        0 ACCEPT     tcp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:55555 
       0        0 ACCEPT     udp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW udp dpts:62000:65535 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            78.129.135.37       tcp dpt:3306 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            217.182.206.73      tcp dpt:3306 
Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      22     1144 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:9007 
     252    32223 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:62000:65535 
       0        0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:9007 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            8.8.4.4             udp spt:53 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            8.8.8.8             tcp dpt:53 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            8.8.8.8             udp dpt:53 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            8.8.8.8             tcp spt:53 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            8.8.8.8             udp spt:53 
     561    39372 LOCALOUTPUT  all  --  *      !lo     0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           tcp dpt:53 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           udp dpt:53 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           tcp spt:53 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           udp spt:53 
       0        0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
     285    28711 INVALID    tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      !lo     0.0.0.0/0            0.0.0.0/0           
     557    38956 ACCEPT     all  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:20 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:21 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:25 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:53 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:80 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:110 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:113 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:443 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2200 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2030 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2031 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2082 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2083 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2086 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2087 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2095 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:2096 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:587 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:993 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:995 
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW tcp dpt:3306 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW udp dpt:20 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW udp dpt:21 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW udp dpt:53 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW udp dpt:113 
       0        0 ACCEPT     udp  --  *      !lo     0.0.0.0/0            0.0.0.0/0           state NEW udp dpt:123 
       0        0 LOGDROPOUT  all  --  *      !lo     0.0.0.0/0            0.0.0.0/0           
Chain ALLOWIN (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  !lo    *       217.147.81.22        0.0.0.0/0           
       0        0 ACCEPT     all  --  !lo    *       83.105.120.173       0.0.0.0/0           
       0        0 ACCEPT     tcp  --  !lo    *       78.129.135.37        0.0.0.0/0           tcp dpt:3306 
       5      320 ACCEPT     all  --  !lo    *       92.236.16.201        0.0.0.0/0           
Chain ALLOWOUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     all  --  *      !lo     0.0.0.0/0            217.147.81.22       
       0        0 ACCEPT     all  --  *      !lo     0.0.0.0/0            83.105.120.173      
       0        0 ACCEPT     tcp  --  *      !lo     0.0.0.0/0            78.129.135.37       tcp dpt:3306 
       4      416 ACCEPT     all  --  *      !lo     0.0.0.0/0            92.236.16.201       
Chain DENYIN (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
Chain DENYOUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
Chain INVALID (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 INVDROP    all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x05/0x05 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x11/0x01 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x18/0x08 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x30/0x20 
       0        0 INVDROP    tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:!0x17/0x02 state NEW 
Chain INVDROP (10 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
Chain LOCALINPUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     610    58169 ALLOWIN    all  --  !lo    *       0.0.0.0/0            0.0.0.0/0           
     605    57849 DENYIN     all  --  !lo    *       0.0.0.0/0            0.0.0.0/0           
Chain LOCALOUTPUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
     561    39372 ALLOWOUT   all  --  *      !lo     0.0.0.0/0            0.0.0.0/0           
     557    38956 DENYOUT    all  --  *      !lo     0.0.0.0/0            0.0.0.0/0           
Chain LOGDROPIN (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:23 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:23 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:67 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:68 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:111 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:111 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:113 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:113 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:135:139 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:135:139 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:445 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:500 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:500 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:513 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:513 
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:520 
       0        0 DROP       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:520 
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 30/min burst 5 LOG flags 0 level 4 prefix `Firewall: *TCP_IN Blocked* ' 
       0        0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 30/min burst 5 LOG flags 0 level 4 prefix `Firewall: *UDP_IN Blocked* ' 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 30/min burst 5 LOG flags 0 level 4 prefix `Firewall: *ICMP_IN Blocked* ' 
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           
Chain LOGDROPOUT (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 30/min burst 5 LOG flags 8 level 4 prefix `Firewall: *TCP_OUT Blocked* ' 
       0        0 LOG        udp  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 30/min burst 5 LOG flags 8 level 4 prefix `Firewall: *UDP_OUT Blocked* ' 
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 30/min burst 5 LOG flags 8 level 4 prefix `Firewall: *ICMP_OUT Blocked* ' 
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 
[root@phoenix-f ~]#
```

---

### Post by Doug S on 2018-07-25
I think you need the OUTPUT chain equivalent to this from your INPUT chain:

```
       0        0 ACCEPT     udp  --  !lo    *       0.0.0.0/0            0.0.0.0/0           state NEW udp dpts:62000:65535
```Assuming it is more than just IP address Y.Y.Y.Y and more then just port 62010 that you want it to work for. Myself, I wouldn't bother with the NOT lo part, but you do what you want.

---

### Post by stewartrose2 on 2018-07-26
Thank you Doug that makes a lot of sense now....

All the best from Alan

---

