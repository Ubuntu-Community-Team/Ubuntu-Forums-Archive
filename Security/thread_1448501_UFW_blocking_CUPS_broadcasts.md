---
title: "UFW blocking CUPS broadcasts"
date: 2010-04-06
forum: Security
---

### Post by jowilkin on 2010-04-06
I cannot get ufw to allow the cups server on my network to broadcast available printers to my machine.

The machine broadcasting is 129.170.65.179, and it broadcasts on 129.170.71.255.  I have tried allowing tcp and udp traffic from both those addresses, but no luck, it's driving me crazy!

Here is ufw status ```
> sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
135/tcp                    ALLOW IN    129.170.64.0/29
139/tcp                    ALLOW IN    129.170.64.0/29
445/tcp                    ALLOW IN    129.170.64.0/29
137/udp                    ALLOW IN    129.170.64.0/29
138/udp                    ALLOW IN    129.170.64.0/29
631                        ALLOW IN    129.170.65.179
631                        ALLOW IN    129.170.71.255
```

And here is part of the everthing.log file ```
Apr  6 17:19:06 theflash kernel: [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:d4:9a:20:f4:19:0a:08:00 SRC=129.170.65.179 DST=129.170.71.255 LEN=175 TOS=0x00 PREC=0x00 TTL=64 ID=17323 PROTO=UDP SPT=631 DPT=631 LEN=155 
Apr  6 17:19:26 theflash kernel: [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:d4:9a:20:f4:19:0a:08:00 SRC=129.170.65.179 DST=129.170.71.255 LEN=194 TOS=0x00 PREC=0x00 TTL=64 ID=19660 PROTO=UDP SPT=631 DPT=631 LEN=174 

```

---

### Post by jowilkin on 2010-04-06
Some output from tcpdump showing that the traffic is present on the network frequently, just not getting to my cups daemon ```
sudo tcpdump -lnn -i eth0 host 129.170.65.179
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
23:41:38.867420 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 136
23:41:39.867758 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 141
23:41:39.867776 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 153
23:41:39.867781 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 136
23:41:41.868235 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 143
23:41:41.868257 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 141
23:41:41.868262 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 145
23:41:42.868773 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 136
23:41:42.868796 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 134
23:41:42.868801 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 151
23:41:42.869045 IP 129.170.65.179.631 > 129.170.71.255.631: UDP, length 152

```

129.170.65.179 is the server that broadcasts cups info and its sending it to the broadcast address 129.170.71.255 on port 631.

---

### Post by jowilkin on 2010-04-07
And here is the iptables output while ufw is enabled ```
> sudo iptables -nvL
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
32884   24M ufw-before-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
32884   24M ufw-before-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 9168 1199K ufw-after-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  148 23639 ufw-after-logging-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  148 23639 ufw-reject-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
  148 23639 ufw-track-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-before-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-before-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-after-logging-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ufw-reject-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
18912 1556K ufw-before-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
18912 1556K ufw-before-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1525 94839 ufw-after-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1525 94839 ufw-after-logging-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1525 94839 ufw-reject-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 1525 94839 ufw-track-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-after-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   15  1170 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:137 
   63 13995 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:138 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:139 
    0     0 ufw-skip-to-policy-input  tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:445 
    1   349 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:67 
    0     0 ufw-skip-to-policy-input  udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:68 
   36  3169 ufw-skip-to-policy-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 

Chain ufw-after-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-after-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-after-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ufw-user-forward  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
  328  450K ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ufw-logging-deny  all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 3 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 4 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 11 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 12 
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 
  175 29096 ufw-not-local  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  *      *       224.0.0.0/4          0.0.0.0/0           
    1    79 ACCEPT     all  --  *      *       0.0.0.0/0            224.0.0.0/4         
  174 29017 ufw-user-input  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-logging-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-before-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
  329 17321 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    1    76 ufw-user-output  all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW ALLOW] ' 

Chain ufw-logging-deny (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID limit: avg 3/min burst 10 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 3/min burst 10 LOG flags 0 level 4 prefix `[UFW BLOCK] ' 

Chain ufw-not-local (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type LOCAL 
    1    79 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type MULTICAST 
  174 29017 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0           ADDRTYPE match dst-type BROADCAST 
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
  115 18683 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-track-output (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 
    1    76 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state NEW 

Chain ufw-user-forward (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain ufw-user-input (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:22 
    0     0 ACCEPT     tcp  --  *      *       129.170.64.0/29      0.0.0.0/0           tcp dpt:135 
    0     0 ACCEPT     tcp  --  *      *       129.170.64.0/29      0.0.0.0/0           tcp dpt:139 
    0     0 ACCEPT     tcp  --  *      *       129.170.64.0/29      0.0.0.0/0           tcp dpt:445 
    0     0 ACCEPT     udp  --  *      *       129.170.64.0/29      0.0.0.0/0           udp dpt:137 
    0     0 ACCEPT     udp  --  *      *       129.170.64.0/29      0.0.0.0/0           udp dpt:138 
    0     0 ACCEPT     tcp  --  *      *       129.170.65.179       0.0.0.0/0           tcp dpt:631 
   59 10334 ACCEPT     udp  --  *      *       129.170.65.179       0.0.0.0/0           udp dpt:631 
    0     0 ACCEPT     tcp  --  *      *       129.170.71.255       0.0.0.0/0           tcp dpt:631 
    0     0 ACCEPT     udp  --  *      *       129.170.71.255       0.0.0.0/0           udp dpt:631 

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

---

### Post by cariboo on 2010-04-07
Firstly, you don't need to allow other systems to access port 631 on the server in order for printing to work, the only thing opening up port 631 does is allow other systems to access the web interface. Can you print from other system if the firewall is disabled? Have you got **Share printers connected to this system** enabled in the cups administration interface?

---

### Post by jowilkin on 2010-04-07
Unless I misread your post, I think you misunderstand my situation.  

I don't have a printer hooked up to my computer, it is not the server.  There is a server on the network here that broadcasts the available printers on the network.  These broadcasts are sent to port 631 as the tcpdump output shows.

So my understanding is I need these broadcasts to get through port 631 on my computer to my cups client so that cups on my computer knows what printers are available on the network.

I can list available printers on the network with the lpstat command.  If firewall is off, I get a large list of printers.  If firewall is on, I get no printers.

---

