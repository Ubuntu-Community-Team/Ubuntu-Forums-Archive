---
title: "World of Warcraft running on Vista thru Ubuntu Server"
date: 2008-07-27
forum: Server Platforms
---

### Post by skipjack on 2008-07-27
Ok, here's the problem...

I recently setup a router/server/firewall configuration using Ubuntu Server (Hardy).  The web surfing work great! No problems at all.  I turned off ipv6, so that shouldn't be a problem.  The problem I am having is that one of the clients Windows Vista (I know)... is running World of Warcraft and the latency is anywhere from 7000-14000 (ridiculous, huh).  Now, The server is on a satellite system, so I'm willing to accept a latency of ~1000, but 7000 just won't work.  I know that I can get better latency by utlizing a d-link router, because that's what was there before I put in the server.  It must be some setting on the server.. Any help would be appreciated..


Configuration:
eth2 - WAN
eth1 - LAN
Using firestarter (first time using this program)
dhcp3-server
openssh
apache2
snmp

Here is some configurations:

Output to route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.221.xx.xx    0.0.0.0         255.255.255.240 U         0 0          0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         10.221.xx.xx    0.0.0.0         UG        0 0          0 eth2

----------------------------------------------------------------
sudo iptables -L OUTPUT:

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  ns2.direcpceu.com    anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  ns2.direcpceu.com    anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
INBOUND    all  --  anywhere             192.168.0.1         
INBOUND    all  --  anywhere             10.221.XX.XX        
INBOUND    all  --  anywhere             192.168.0.255       
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN TCPMSS clamp to PMTU 
OUTBOUND   all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             192.168.0.0/24      state RELATED,ESTABLISHED 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  10.221.XX.XX         XXX.XXXXXXXXX.com   tcp dpt:domain 
ACCEPT     udp  --  10.221.XX.XX         XXX.XXXXXXXXX.com   udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (4 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  206.17.111.115       anywhere            
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:ssh 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:ssh 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:www 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:www 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:ftp-data:ftp 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:20:fsp 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:pop3 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:pop3 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:netbios-ns:netbios-ssn 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:netbios-ns:netbios-ssn 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:microsoft-ds 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:microsoft-ds 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:https 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:https 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:smtp 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:25 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:6901 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:6901 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:6891 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:6891 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:6900 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:6900 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:3724 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:3724 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:aol 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:aol 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpt:6112 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpt:6112 
ACCEPT     tcp  --  192.168.0.0/24       anywhere            tcp dpts:6881:6999 
ACCEPT     udp  --  192.168.0.0/24       anywhere            udp dpts:6881:6999 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (3 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere      

----------------------------------------------------------------
ip a |grep inet6 OUTPUT:
NOTHING
---------------------------------------------------------------
ifconfig OUTPUT:
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:9b:33:db  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:11:3b:0e:a5:eb  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39333315 (37.5 MB)  TX bytes:5746443 (5.4 MB)
          Interrupt:20 Base address:0xd000 

eth2      Link encap:Ethernet  HWaddr 00:11:3b:0e:c0:dd  
          inet addr:10.221.XX.XX  Bcast:255.255.255.255  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7666557 (7.3 MB)  TX bytes:39389892 (37.5 MB)
          Interrupt:17 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68085 (66.4 KB)  TX bytes:68085 (66.4 KB)

Any help would be greatly appreciated!!

---

### Post by yeaitsdark on 2008-07-27
As far as my thinking can take me is that games are often very inconsiderate of firewalls. Up until a couple days ago I was using a linux machine with iptables and the like, but after some NAT and port forwarding headaches with iptables, and my friend giving me a free linksys rv082 (quite a nice router with loads of options), I decided the heck with using this I'll use this router instead of my computer - as a router.

But I'm quite sure you have your reasons for using your machine in the way that you are. So, that being said, one "issue" I had with firestarter and iptables, was that I had to do everything twice. In other words, I say iptables it's ok to let 8767 for teamspeak to come through and also send it to 10.0.0.x please. Then, I'd have to open the firestarter gui (I never had to use command line btw, as I don't know if you have a gui or not) then I would say ok, all traffic from each lan IP is allowed, and also allow 8767 to come through as well. Apply. OK. Then, it would work.

In short, (I'm long-winded) - I would double check and make sure you have all the wow ports forwarded via iptables AND firestarter [http://portforward.com/cportsnotes/battlenet/wow.htm](http://portforward.com/cportsnotes/battlenet/wow.htm) and also check that you don't have some crazy NAT problems, I'm guessing firestarter is doing NAT? Because, well I think it's a forwarding issue. Lag due to a lot of negotiations and network traversal perhaps.

Anyways hope that helps a bit.

---

### Post by skipjack on 2008-07-27
yeaitsdark, first of all, thanks for the reply!  I do agree with on about gaming software not being consistent as I've noticed while troubleshooting this problem. (First time troubleshooting games via a LAN, I'm used to working with business software that only does what it's told).  Anyway, I will try what you said and double tap all the settings.  If you or anyone else comes up with something else to try... I'm all ears, this one is killing me...lol!  Thanks again.

-skipjack

---

### Post by skipjack on 2008-07-27
Ok, it's fixed!  The way I solved the problem was to use shorewall.  I really like how simple it is....

yeaitsdark, thanks for the response and the help!  

I really don't know why firestarter didn't do the job, but oh well.  

-skipjack

---

### Post by yeaitsdark on 2008-07-27
Ahh good to hear. Yea, as I said, I was having a lot of issues with like "dual" firewalls almost between firestarter and iptables, (mind you I'm no iptable expert, and I'll bet not many people are, lol, headache they are).

It's always that checkmark or option you least expect it seems haha.

---

