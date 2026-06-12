---
title: "Cant ping server and website but website doesnt load"
date: 2014-05-01
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-05-01
Some of my websites don't load after I moved server.
My server has two ip addresses. The websites which don't load are all on ip 111.90.150.93
Here are traceroute and ping results

astarmathsandphysics@SERVER:~$ traceroute thexxxxxxxxxxx.info
traceroute to theeducationchannel.info (111.90.150.93), 30 hops max, 60 byte packets
 1  routerlogin.net (192.168.0.1)  0.586 ms  1.478 ms  2.279 ms
 2  10.240.76.1 (10.240.76.1)  24.987 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * te13-4.br02.ldn01.pccwbtn.net (195.66.236.167)  27.563 ms
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *
astarmathsandphysics@SERVER:~$ ping thxxxxxxxxx.info
PING theeducationchannel.info (111.90.150.93) 56(84) bytes of data.
^C
--- theeducationchannel.info ping statistics ---
150 packets transmitted, 0 received, 100% packet loss, time 148965ms

astarmathsandphysics@SERVER:~$

The ip address alsop has 100% packet loss

---

### Post by volkswagner on 2014-05-01
Do you have a network interfaces setup with this ip address?
Post contents for /etc/network/interfaces.

If you are running a firewall, this may also be blocking it.
What's the output of:
```
iptables -L
```

EDIT:
Well it appears that ip is now responding.
Please let us know what you did to fix it for completeness, and you may also mark the thread as solved.

---

### Post by astarmathsandphysics on 2014-05-01
The ip address alsop has 100% packet loss

Here is something from my apache log

[01/May/2014:06:21:39 -0400] "GET /theexxxxxxxxl/player/cbplayer/player.swf?config=http%3A%2F%2xxxxxxxxel.info%2Ftxxxxxxel%2Fplayer%2Fcbplayer%2Fembed_player.php%3Fvid%3D963%26autoplay%3Dyes HTTP/1.1" 404 3126 "-" "Googlebot-Video/1.0"

Here is the file /etc/network/interfaces

  GNU nano 2.2.6                   File: /etc/network/interfaces                                  Modified  

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth0:1
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
        address 111.90.150.92
        netmask 255.255.255.0
        network 111.90.150.0
        broadcast 111.90.150.255
        gateway 111.90.150.1
allow-hotplug eth0:1
iface eth0:1 inet static
        address 111.90.150.93
        netmask 255.255.255.0
        network 111.90.150.0
        broadcast 111.90.150.255
        gateway 111.90.150.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 193.109.68.87 141.105.64.118
        dns-search

And here is the output from iptables -L

 dpts:1024:65534 reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spts:1024:65534 dpts:6881:6889 reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spts:6881:6889 dpts:1024:65534 reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere             tcp dpt:gnutella-svc reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere             tcp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spts:1024:65534 dpt:gnutella-svc reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spt:gnutella-svc dpts:1024:65534 reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere             tcp dpt:7778 reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere             tcp spt:7778 dpts:1024:65534 reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spts:1024:65534 dpt:7778 reject-with icmp-port-unreachable
REJECT     udp  --  anywhere             anywhere             udp spt:7778 dpts:1024:65534 reject-with icmp-port-unreachable

Chain PROHIBIT (0 references)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere             reject-with icmp-host-prohibited

Chain PZERO (2 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere             tcp dpt:0
DROP       udp  --  anywhere             anywhere             udp dpt:0
DROP       tcp  --  anywhere             anywhere             tcp spt:0
DROP       udp  --  anywhere             anywhere             udp spt:0

Chain REFRESH_TEMP (2 references)
target     prot opt source               destination         

Chain RESET (0 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere             reject-with tcp-reset

Chain TALLOW (2 references)
target     prot opt source               destination         

Chain TDENY (2 references)
target     prot opt source               destination         
DROP       all  --  175.44.6.239         anywhere            
DROP       all  --  anywhere             175.44.6.239        
DROP       all  --  ns300183.ovh.net     anywhere            
DROP       all  --  anywhere             ns300183.ovh.net    
DROP       all  --  ns207459.ovh.net     anywhere            
DROP       all  --  anywhere             ns207459.ovh.net    
DROP       all  --  esparta.localizaweb.com.br  anywhere            
DROP       all  --  anywhere             esparta.localizaweb.com.br 
DROP       all  --  ns384429.ovh.net     anywhere            
DROP       all  --  anywhere             ns384429.ovh.net    
DROP       all  --  ns28679.ovh.net      anywhere            
DROP       all  --  anywhere             ns28679.ovh.net     
DROP       all  --  27.12.212.154        anywhere            
DROP       all  --  anywhere             27.12.212.154       
DROP       all  --  ec2-54-194-107-120.eu-west-1.compute.amazonaws.com  anywhere            
DROP       all  --  anywhere             ec2-54-194-107-120.eu-west-1.compute.amazonaws.com 
DROP       all  --  ns366835.ovh.net     anywhere            
DROP       all  --  anywhere             ns366835.ovh.net    
DROP       all  --  ns389755.ovh.net     anywhere            
DROP       all  --  anywhere             ns389755.ovh.net    
DROP       all  --  ns367541.ovh.net     anywhere            
DROP       all  --  anywhere             ns367541.ovh.net    
DROP       all  --  175.44.10.183        anywhere            
DROP       all  --  anywhere             175.44.10.183       
DROP       all  --  112.111.172.33       anywhere            
DROP       all  --  anywhere             112.111.172.33      
DROP       all  --  183.16.200.28        anywhere            
DROP       all  --  anywhere             183.16.200.28       
DROP       all  --  175.44.8.86          anywhere            
DROP       all  --  anywhere             175.44.8.86         
DROP       all  --  ns23561.ovh.net      anywhere            
DROP       all  --  anywhere             ns23561.ovh.net     
DROP       all  --  112.111.173.164      anywhere            
DROP       all  --  anywhere             112.111.173.164     
DROP       all  --  [www.gogmailer.com](www.gogmailer.com)    anywhere            
DROP       all  --  anywhere             [www.gogmailer.com](www.gogmailer.com)   
DROP       all  --  112.111.172.146      anywhere            
DROP       all  --  anywhere             112.111.172.146     
DROP       all  --  198-1-68-250.unifiedlayer.com  anywhere            
DROP       all  --  anywhere             198-1-68-250.unifiedlayer.com 
DROP       all  --  192.111.145.13       anywhere            
DROP       all  --  anywhere             192.111.145.13      
DROP       all  --  host201-89-206-24.limes.com.pl  anywhere            
DROP       all  --  anywhere             host201-89-206-24.limes.com.pl 
DROP       all  --  net1.netdominios.com.br  anywhere            
DROP       all  --  anywhere             net1.netdominios.com.br 
DROP       all  --  ns1.tecway.com.br    anywhere            
DROP       all  --  anywhere             ns1.tecway.com.br   
DROP       all  --  ns302173.ovh.net     anywhere            
DROP       all  --  anywhere             ns302173.ovh.net    
DROP       all  --  7c29556f.i-revonet.jp  anywhere            
DROP       all  --  anywhere             7c29556f.i-revonet.jp 
DROP       all  --  server03.hostingcia.info  anywhere            
DROP       all  --  anywhere             server03.hostingcia.info 
^ADROP       all  --  58.251.146.238       anywhere            
DROP       all  --  anywhere             reverse.gdsz.cncnet.net 
DROP       all  --  hn.kd.ny.adsl        anywhere            
DROP       all  --  anywhere             hn.kd.ny.adsl       
DROP       all  --  onitdigital.com      anywhere            
DROP       all  --  anywhere             onitdigital.com     
DROP       all  --  116.255.164.99       anywhere            
DROP       all  --  anywhere             116.255.164.99      
DROP       all  --  192.111.152.86       anywhere            
DROP       all  --  anywhere             192.111.152.86      
DROP       all  --  111.37.11.56         anywhere            
DROP       all  --  anywhere             111.37.11.56        
DROP       all  --  119.176.50.181       anywhere            
DROP       all  --  anywhere             119.176.50.181      
DROP       all  --  sakura.gridol.net    anywhere            
DROP       all  --  anywhere             sakura.gridol.net   
DROP       all  --  62.37.237.1          anywhere            
DROP       all  --  anywhere             62.37.237.1         
DROP       all  --  200-69-162-69.static.reverse.lstn.net  anywhere            
DROP       all  --  anywhere             200-69-162-69.static.reverse.lstn.net 
DROP       all  --  91.233.246.225       anywhere            
DROP       all  --  anywhere             91.233.246.225      
DROP       all  --  58.254.168.75        anywhere            
DROP       all  --  anywhere             58.254.168.75       
DROP       all  --  175.44.5.210         anywhere            
DROP       all  --  anywhere             175.44.5.210        
DROP       all  --  124.42.247.250       anywhere            
DROP       all  --  anywhere             124.42.247.250      
DROP       all  --  122.13.132.51        anywhere            
DROP       all  --  anywhere             122.13.132.51       
DROP       all  --  117.44.166.183       anywhere            
DROP       all  --  anywhere             117.44.166.183      
DROP       all  --  61.160.215.223       anywhere            
DROP       all  --  anywhere             61.160.215.223      
DROP       all  --  ns38407.ovh.net      anywhere            
DROP       all  --  anywhere             ns38407.ovh.net     
DROP       all  --  112.111.174.174      anywhere            
DROP       all  --  anywhere             112.111.174.174     
DROP       all  --  112.111.173.50       anywhere            
DROP       all  --  anywhere             112.111.173.50      
DROP       all  --  112.111.172.92       anywhere            
DROP       all  --  anywhere             112.111.172.92      
DROP       all  --  112.111.175.60       anywhere            
DROP       all  --  anywhere             112.111.175.60      
DROP       all  --  220-133-175-190.HINET-IP.hinet.net  anywhere            
DROP       all  --  anywhere             220-133-175-190.HINET-IP.hinet.net 
DROP       all  --  60-251-146-242.HINET-IP.hinet.net  anywhere            
DROP       all  --  anywhere             60-251-146-242.HINET-IP.hinet.net 
DROP       all  --  101.17.52.253        anywhere            
DROP       all  --  anywhere             101.17.52.253       
DROP       all  --  datacenter.lgvhost.com.br  anywhere            
DROP       all  --  anywhere             datacenter.lgvhost.com.br 
DROP       all  --  74-95-10-210-SFBA.hfc.comcastbusiness.net  anywhere            
DROP       all  --  anywhere             74-95-10-210-SFBA.hfc.comcastbusiness.net 
DROP       all  --  111-243-169-32.dynamic.hinet.net  anywhere            
DROP       all  --  anywhere             111-243-169-32.dynamic.hinet.net 
DROP       all  --  112.111.173.248      anywhere            
DROP       all  --  anywhere             112.111.173.248     
DROP       all  --  sv135d210.static.dc.ngoinhamang.com  anywhere            
DROP       all  --  anywhere             sv135d210.static.dc.ngoinhamang.com 
DROP       all  --  112.111.175.146      anywhere            
DROP       all  --  anywhere             112.111.175.146     
DROP       all  --  122.13.132.54        anywhere            
DROP       all  --  anywhere             122.13.132.54       
DROP       all  --  183.219.30.108       anywhere            
DROP       all  --  anywhere             183.219.30.108      
DROP       all  --  223.16.137.42        anywhere            
DROP       all  --  anywhere             223.16.137.42       
DROP       all  --  60-241-222-202.static.tpgi.com.au  anywhere            
DROP       all  --  anywhere             60-241-222-202.static.tpgi.com.au 
DROP       all  --  ka4ek.vds            anywhere            
DROP       all  --  anywhere             ka4ek.vds           
DROP       all  --  124.42.244.43        anywhere            
DROP       all  --  anywhere             124.42.244.43       
DROP       all  --  180.166.7.134        anywhere            
DROP       all  --  anywhere             180.166.7.134       
DROP       all  --  90.67.95.117.broad.ha.js.dynamic.163data.com.cn  anywhere            
DROP       all  --  anywhere             90.67.95.117.broad.ha.js.dynamic.163data.com.cn 
DROP       all  --  175.44.5.248         anywhere            
DROP       all  --  anywhere             175.44.5.248        
DROP       all  --  175.44.7.64          anywhere            
DROP       all  --  anywhere             175.44.7.64         
DROP       all  --  175.44.4.5           anywhere            
DROP       all  --  anywhere             175.44.4.5          
DROP       all  --  175.44.7.80          anywhere            
DROP       all  --  anywhere             175.44.7.80         
DROP       all  --  175.44.8.52          anywhere            
DROP       all  --  anywhere             175.44.8.52         
DROP       all  --  116.24.21.21         anywhere            
DROP       all  --  anywhere             116.24.21.21        

Chain TGALLOW (2 references)
target     prot opt source               destination         

Chain TGDENY (2 references)
target     prot opt source               destination         
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  li679-170.members.linode.com  anywhere            
DROP       all  --  anywhere             li679-170.members.linode.com 
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  li679-170.members.linode.com  anywhere            
DROP       all  --  anywhere             li679-170.members.linode.com 
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  li679-170.members.linode.com  anywhere            
DROP       all  --  anywhere             li679-170.members.linode.com 
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  mb.tdc.to            anywhere            
DROP       all  --  anywhere             mb.tdc.to           
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  mb.tdc.to            anywhere            
DROP       all  --  anywhere             mb.tdc.to           
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  li679-170.members.linode.com  anywhere            
DROP       all  --  anywhere             li679-170.members.linode.com 
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  mb.tdc.to            anywhere            
DROP       all  --  anywhere             mb.tdc.to           
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  li679-170.members.linode.com  anywhere            
DROP       all  --  anywhere             li679-170.members.linode.com 
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  mb.tdc.to            anywhere            
DROP       all  --  anywhere             mb.tdc.to           
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18       
DROP       all  --  218.93.250.18        anywhere            
DROP       all  --  anywhere             218.93.250.18

here are replies to ifconfig and route in terminal

root@server11362:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 70:54:d2:16:a7:a3  
          inet addr:111.90.150.92  Bcast:111.90.150.255  Mask:255.255.255.0
          inet6 addr: fe80::7254:d2ff:fe16:a7a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45049842 errors:0 dropped:186329 overruns:0 frame:0
          TX packets:46536516 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5495842599 (5.4 GB)  TX bytes:59100672444 (59.1 GB)
          Interrupt:20 Memory:fe400000-fe420000 

eth0:1    Link encap:Ethernet  HWaddr 70:54:d2:16:a7:a3  
          inet addr:111.90.150.93  Bcast:111.90.150.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8817446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8817446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78859684003 (78.8 GB)  TX bytes:78859684003 (78.8 GB)

root@server11362:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         111.90.150.1    0.0.0.0         UG    100    0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth0
root@server11362:~#

> **volkswagner said:**
> Do you have a network interfaces setup with this ip address?
Post contents for /etc/network/interfaces.

If you are running a firewall, this may also be blocking it.
What's the output of:
```
iptables -L
```

EDIT:
Well it appears that ip is now responding.
Please let us know what you did to fix it for completeness, and you may also mark the thread as solved.

Is it responding? I still get 100% packet loss

i can access the ip from within the local network.
and the website too

root@server11362:~# ping 111.90.150.93
PING 111.90.150.93 (111.90.150.93) 56(84) bytes of data.
64 bytes from 111.90.150.93: icmp_req=1 ttl=64 time=0.045 ms
64 bytes from 111.90.150.93: icmp_req=2 ttl=64 time=0.026 ms
64 bytes from 111.90.150.93: icmp_req=3 ttl=64 time=0.029 ms
64 bytes from 111.90.150.93: icmp_req=4 ttl=64 time=0.026 ms
64 bytes from 111.90.150.93: icmp_req=5 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=6 ttl=64 time=0.030 ms
64 bytes from 111.90.150.93: icmp_req=7 ttl=64 time=0.030 ms
64 bytes from 111.90.150.93: icmp_req=8 ttl=64 time=0.030 ms
64 bytes from 111.90.150.93: icmp_req=9 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=10 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=11 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=12 ttl=64 time=0.033 ms
64 bytes from 111.90.150.93: icmp_req=13 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=14 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=15 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=16 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=17 ttl=64 time=0.034 ms
64 bytes from 111.90.150.93: icmp_req=18 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=19 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=20 ttl=64 time=0.025 ms
64 bytes from 111.90.150.93: icmp_req=21 ttl=64 time=0.033 ms
64 bytes from 111.90.150.93: icmp_req=22 ttl=64 time=0.032 ms
64 bytes from 111.90.150.93: icmp_req=23 ttl=64 time=0.033 ms
64 bytes from 111.90.150.93: icmp_req=24 ttl=64 time=0.028 ms
64 bytes from 111.90.150.93: icmp_req=25 ttl=64 time=0.030 ms
64 bytes from 111.90.150.93: icmp_req=26 ttl=64 time=0.030 ms
64 bytes from 111.90.150.93: icmp_req=27 ttl=64 time=0.031 ms
64 bytes from 111.90.150.93: icmp_req=28 ttl=64 time=0.030 ms
^C
--- 111.90.150.93 ping statistics ---
28 packets transmitted, 28 received, 0% packet loss, time 26996ms
rtt min/avg/max/mdev = 0.025/0.031/0.045/0.004 ms
root@server11362:~# traceroute thxxxxxxxxx.info
traceroute to theeducationchannel.info (111.90.150.93), 30 hops max, 60 byte packets
 1  111.90.150.93 (111.90.150.93)  0.027 ms  0.015 ms  0.008 ms
root@server11362:~#

result from arp -n 

root@server11362:~# arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
111.90.150.1             ether   00:19:b9:f8:d8:8f   C                     eth0

---

### Post by SeijiSensei on 2014-05-02
That address is pingable from here in Boston.  I can telnet to port 80 at that address as well. Opening theeducationchannel.info in a browser gives me a message that you're updating your site.

---

### Post by astarmathsandphysics on 2014-05-02
Are eth0 and eth0:1 two physical cables or one cable enabling 2 ip addresses?

Well thank god for that
I am moving forward 1mm at a time
My host took two months to discover that dns wasnt properly set up as well, leaving me to think the problem was on my server.

NOt I am making real progress with this.
My websites on 111.90.150.93 load on my phone but not my pc.
It may be some dns issue on home pc. The server is newly installed and the ip was on a blacklist. If my isp is blocking it now, it will soon be unblocked. 
eITHER WAY i FEEL VERY CONFIDENT NOW AND THANKS.

---

### Post by Doug S on 2014-05-04
> **SeijiSensei said:**
> That address is pingable from here in Boston.  I can telnet to port 80 at that address as well. Opening theeducationchannel.info in a browser gives me a message that you're updating your site.Intersting. I can NOT ping it from here near Vancouver Canada, nor does trying to open theeducationchannel.info in a browser. I have tried 3 times over about 12 hours. Forward DNS lookup works, but reverse DNS lookup does not.

---

