---
title: "Problem With Firestarter"
date: 2009-09-23
forum: Security
---

### Post by MStanchev on 2009-09-23
Hello from me,first of all sorry for my bad English.
Here is my question:
Before 2 days I install Ubuntu 9.04,after reading some tutorials,I decided to install Firestarter using add/ remove manager.Everything seems to be ok,until now:
When I start Firestarter in a Policy windows a have rule aboute allowing connection from Russian ip adress:
[IMG]http://img225.imageshack.us/img225/7025/screenshotfirestartermi.png[/IMG]
I am never allow this ip,is there anything i can worry about this ip?
Another problem is that Firestarter show in event window that block around 5 ip every minutes,I have public ip visible all around the world.
Thanks for answers.:KS

---

### Post by Soul-Sing on 2009-09-23
What is the outcome of: ```
sudo iptables -L -v
```

---

### Post by Soul-Sing on 2009-09-23
Ps: maybe it is better to install ufw or gufw. Firestarter isn't maintained for several years.

To block single ip's: ```
sudo ufw deny from <ipadress>
```
If you try gufw please uninstall firestarter first.

---

### Post by MStanchev on 2009-09-23
Here its wnen type:
sudo iptables -L -v 
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     mail.networx-bg.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
    0     0 ACCEPT     udp  --  any    any     mail.networx-bg.com  anywhere            
    0     0 ACCEPT     tcp  --  any    any     zlokobni.networx-bg.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
    0     0 ACCEPT     udp  --  any    any     zlokobni.networx-bg.com  anywhere            
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 DROP       all  --  ppp0   any     anywhere             255.255.255.255     
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    0     0 LSI        all  -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5 
   48  3031 INBOUND    all  --  ppp0   any     anywhere             anywhere            
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  mail.networx-bg.com tcp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  mail.networx-bg.com udp dpt:domain 
    0     0 ACCEPT     tcp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  zlokobni.networx-bg.com tcp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  zlokobni.networx-bg.com udp dpt:domain 
    0     0 ACCEPT     all  --  any    lo      anywhere             anywhere            
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    0     0 OUTBOUND   all  --  any    ppp0    anywhere             anywhere            
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  any    any     ppp91-77-246-135.pppoe.mtu-net.ru  anywhere            
   20  1195 LSI        all  --  any    any     anywhere             anywhere            

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   48  3031 LOG_FILTER  all  --  any    any     anywhere             anywhere            
   36  1744 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
   36  1744 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 
   12  1287 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
   12  1287 DROP       all  --  any    any     anywhere             anywhere            

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
    0     0 REJECT     all  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  any    any     anywhere             anywhere 
```Thanks for reply [leoquant]("http://ubuntuforums.org/member.php?u=155157") I will try your suggestion in second post here. :)

---

### Post by MStanchev on 2009-09-23
I find this code in my previous post,maybe this is the problem:
    0     0 ACCEPT     all  --  any    any     ppp91-77-246-135.pppoe.mtu-net.ru  anywhere

---

### Post by Soul-Sing on 2009-09-23
By the way your firewall (iptables) is up and running with firestarter. There no great problems afaik.
Maybe you can block this ru-ipadress with firestarter?

---

### Post by MStanchev on 2009-09-23
> **leoquant said:**
> By the way your firewall (iptables) is up and running with firestarter. There no great problems afaik.
Maybe you can block this ru-ipadress with firestarter?
Yes, I remove the rule in firestarter and block this ip,now it seem to be ok.:)
```
Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     zlokobni.networx-bg.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
    1   389 ACCEPT     udp  --  any    any     zlokobni.networx-bg.com  anywhere            
    0     0 ACCEPT     tcp  --  any    any     mail.networx-bg.com  anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
    0     0 ACCEPT     udp  --  any    any     mail.networx-bg.com  anywhere            
    0     0 ACCEPT     all  --  lo     any     anywhere             anywhere            
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 DROP       all  --  ppp0   any     anywhere             255.255.255.255     
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    0     0 LSI        all  -f  any    any     anywhere             anywhere            limit: avg 10/min burst 5 
   23  2946 INBOUND    all  --  ppp0   any     anywhere             anywhere            
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  zlokobni.networx-bg.com tcp dpt:domain 
    1    77 ACCEPT     udp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  zlokobni.networx-bg.com udp dpt:domain 
    0     0 ACCEPT     tcp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  mail.networx-bg.com tcp dpt:domain 
    0     0 ACCEPT     udp  --  any    any     zdravec-iztok-unl-ip76.networx-bg.com  mail.networx-bg.com udp dpt:domain 
    0     0 ACCEPT     all  --  any    lo      anywhere             anywhere            
    0     0 DROP       all  --  any    any     BASE-ADDRESS.MCAST.NET/8  anywhere            
    0     0 DROP       all  --  any    any     anywhere             BASE-ADDRESS.MCAST.NET/8 
    0     0 DROP       all  --  any    any     255.255.255.255      anywhere            
    0     0 DROP       all  --  any    any     anywhere             0.0.0.0             
    0     0 DROP       all  --  any    any     anywhere             anywhere            state INVALID 
    5  1004 OUTBOUND   all  --  any    ppp0    anywhere             anywhere            
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4  1946 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
   19  1000 LSI        all  --  any    any     anywhere             anywhere            

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
   19  1000 LOG_FILTER  all  --  any    any     anywhere             anywhere            
   12   584 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
   12   584 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
    0     0 LOG        tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       tcp  --  any    any     anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
    0     0 LOG        icmp --  any    any     anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
    0     0 DROP       icmp --  any    any     anywhere             anywhere            icmp echo-request 
    7   416 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
    7   416 DROP       all  --  any    any     anywhere             anywhere            

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  any    any     anywhere             anywhere            
    0     0 LOG        all  --  any    any     anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
    0     0 REJECT     all  --  any    any     anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  any    any     anywhere             anywhere            
    4   960 ACCEPT     tcp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere            state RELATED,ESTABLISHED 
    1    44 ACCEPT     all  --  any    any     anywhere             anywhere  F
```
Later I will try gufw anyway,thanks for reply.

---

