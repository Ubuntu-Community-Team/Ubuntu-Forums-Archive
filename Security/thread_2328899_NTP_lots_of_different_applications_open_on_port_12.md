---
title: "NTP lots of different applications open on port 123"
date: 2016-06-25
forum: Security
---

### Post by jammydodger2 on 2016-06-25
Hi All 
Is their a alternative to NTP have lots of applications listening on port 123 
Do I need all these ,also have mythtv (for other users that might run this application )seems also to have lots open running on laptop only frontend and backend no additional packages mythweb etc just tv

```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:6544          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:6549          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:6554          0.0.0.0:*               LISTEN     
tcp        1      0 192.168.0.10:41618      162.213.33.48:443       CLOSE_WAIT 
tcp6       0      0 fe80::f24b:931f:4b:6543 :::*                    LISTEN     
tcp6       0      0 ::1:6543                :::*                    LISTEN     
tcp6       0      0 fe80::f24b:931f:4b:6544 :::*                    LISTEN     
tcp6       0      0 ::1:6544                :::*                    LISTEN     
tcp6       0      0 fe80::f24b:931f:4b:6549 :::*                    LISTEN     
tcp6       0      0 ::1:6549                :::*                    LISTEN     
tcp6       0      0 fe80::f24b:931f:4b:6554 :::*                    LISTEN     
tcp6       0      0 ::1:6554                :::*                    LISTEN     
udp        0      0 255.255.255.255:1900    0.0.0.0:*                          
udp        0      0 239.255.255.250:1900    0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 192.168.0.3:123         0.0.0.0:*                          
udp        0      0 192.168.0.10:123        0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 fd34:1216:9b2:0:35e:123 :::*                               
udp6       0      0 fd34:1216:9b2:0:141:123 :::*                               
udp6       0      0 fe80::a243:c901:f5f:123 :::*                               
udp6       0      0 fd34:1216:9b2:0:385:123 :::*                               
udp6       0      0 fe80::f24b:931f:4ba:123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 fd34:1216:9b2:0:6c5:123 :::*                               
udp6       0      0 ::1:123                 :::*                               
udp6       0      0 :::123                  :::*            
tcp        0      0 localhost:mysql         *:*                     LISTEN      896/mysqld      
tcp        0      0 localhost:6543          *:*                     LISTEN      890/mythbackend 
tcp        0      0 localhost:6544          *:*                     LISTEN      890/mythbackend 
tcp        0      0 localhost:6549          *:*                     LISTEN      890/mythbackend 
tcp        0      0 localhost:6554          *:*                     LISTEN      890/mythbackend 
tcp        1      0 ***********:41618 productsearch.ubu:https CLOSE_WAIT  2544/unity-scope-ho
tcp6       0      0 fe80::f24b:931f:4b:6543 [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 ip6-localhost:6543      [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 fe80::f24b:931f:4b:6544 [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 ip6-localhost:6544      [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 fe80::f24b:931f:4b:6549 [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 ip6-localhost:6549      [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 fe80::f24b:931f:4b:6554 [::]:*                  LISTEN      890/mythbackend 
tcp6       0      0 ip6-localhost:6554      [::]:*                  LISTEN      890/mythbackend 
udp        0      0 255.255.255.255:1900    *:*                                 890/mythbackend 
udp        0      0 239.255.255.250:1900    *:*                                 890/mythbackend 
udp        0      0 *:bootpc                *:*                                 1636/dhclient   
udp        0      0 *:bootpc                *:*                                 963/dhclient    
udp        0      0 ******************:ntp *:*                                 1224/ntpd       
udp        0      0 *******************-CQ6:ntp *:*                                 1224/ntpd       
udp        0      0 localhost:ntp           *:*                                 1224/ntpd       
udp        0      0 *:ntp                   *:*                                 1224/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1224/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1224/ntpd       
udp6       0      0 fd34:1216:9b2:0:35e:ntp [::]:*                              1224/ntpd       
udp6       0      0 fd34:1216:9b2:0:141:ntp [::]:*                              1224/ntpd       
udp6       0      0 fe80::a243:c901:f5f:ntp [::]:*                              1224/ntpd       
udp6       0      0 fd34:1216:9b2:0:385:ntp [::]:*                              1224/ntpd       
udp6       0      0 fe80::f24b:931f:4ba:ntp [::]:*                              1224/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1224/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1224/ntpd       
udp6       0      0 fd34:1216:9b2:0:6c5:ntp [::]:*                              1224/ntpd       
udp6       0      0 ip6-localhost:ntp       [::]:*                              1224/ntpd       
udp6       0      0 [::]:ntp                [::]:*      
```

Any help appreciated

---

### Post by TheFu on 2016-06-26
From what you've posted, it looks like 1 daemon listening on every IP the machine has. Nothing strange about that.
If you aren't using IPv6, disable it. It is just another attack vector.

**$ sudo lsof |grep ntp |grep IPv4**
on my systems shows only 1 PID, listening on 4 different connects and 1 of those is the network broadcast.

I run an NTP server internally for all the other systems to use. On that machine, it is the same single, process too:
```
$ sudo lsof |grep ntp |grep IPv4
ntpd       2614                   ntp   16u     IPv4              14815          0t0        UDP *:ntp 
ntpd       2614                   ntp   18u     IPv4              14822          0t0        UDP localhost:ntp 
ntpd       2614                   ntp   19u     IPv4              14823          0t0        UDP romulus:ntp 
ntpd       2614                   ntp   24u     IPv4              16156          0t0        UDP 192.168.122.1:ntp 

```
The .122.1 IP is for virtual machines - I don't actually use it.  If you'd like to limit which interfaces that ntpd binds with, I bet there is a setting for that.

I don't enable IPv6 here simply because I'm not ready for it, especially with all the firewall rules that would be necessary. Plus, my ISP doesn't provide IPv6 static subnets (don't ask me why). When they do, I'll switch quickly.

In short, I wouldn't worry about it, but it could be something really, really, bad. I'd have to look at some systems monitoring to see how the ntp process(es) are impacting other things.

BTW, would be helpful if you showed the exact command run AND the output together.  That way people with more experience can see if what the command does is really what you intended. Code tags would help too - so things line up and are easier to read.

---

### Post by jammydodger2 on 2016-06-29
My Internet provider is sky broadband I dont know if they are using IPV6
would like to close it down if not,happy to provide any logs with regards to resources using NTP

ifconfig

```
enp3s0    Link encap:Ethernet  HWaddr 00:26:9e:55:78:85  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fd34:1216:9b2:0:ded:f5a7:965f:c132/64 Scope:Global
          inet6 addr: 2a02:c7d:b5d3:8f00:e8b9:c224:465d:3ecc/64 Scope:Global
          inet6 addr: 2a02:c7d:b5d3:8f00:ded:f5a7:965f:c132/64 Scope:Global
          inet6 addr: fd34:1216:9b2:0:5260:8ca8:229f:2cf5/64 Scope:Global
          inet6 addr: fe80::e8a5:320f:a756:bcea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7989326 (7.9 MB)  TX bytes:2435249 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:4972 (4.9 KB)  TX bytes:4972 (4.9 KB)

wlp2s0    Link encap:Ethernet  HWaddr 0c:60:76:53:42:29  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:c7d:b5d3:8f00:dfe9:4a62:903f:a641/64 Scope:Global
          inet6 addr: fd34:1216:9b2:0:35ec:9651:bc18:9ef8/64 Scope:Global
          inet6 addr: fd34:1216:9b2:0:b8fc:f1e4:db78:d22f/64 Scope:Global
          inet6 addr: fe80::a243:c901:f5f6:cabe/64 Scope:Link
          inet6 addr: 2a02:c7d:b5d3:8f00:b8fc:f1e4:db78:d22f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3962 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1318936 (1.3 MB)  TX bytes:15790 (15.7 KB)

```

$ sudo netstat -taun

```
~
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:6543          0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.10:48020      52.38.186.128:443       TIME_WAIT  
tcp        0      0 192.168.0.10:50724      104.16.112.18:443       ESTABLISHED
tcp        0      0 192.168.0.10:36160      151.101.129.69:80       ESTABLISHED
tcp        1      0 192.168.0.10:60856      162.213.33.49:443       CLOSE_WAIT 
tcp6       0      0 ::1:6543                :::*                    LISTEN     
udp        0      0 255.255.255.255:1900    0.0.0.0:*                          
udp        0      0 239.255.255.250:1900    0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 192.168.0.3:123         0.0.0.0:*                          
udp        0      0 192.168.0.10:123        0.0.0.0:*                          
udp        0      0 127.0.0.1:123           0.0.0.0:*                          
udp        0      0 0.0.0.0:123             0.0.0.0:*                          
udp6       0      0 fe80::a243:c901:f5f:123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 fd34:1216:9b2:0:35e:123 :::*                               
udp6       0      0 fd34:1216:9b2:0:b8f:123 :::*                               
udp6       0      0 fe80::e8a5:320f:a75:123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 2a02:c7d:b5d3:8f00::123 :::*                               
udp6       0      0 fd34:1216:9b2:0:526:123 :::*                               
udp6       0      0 fd34:1216:9b2:0:ded:123 :::*                               
udp6       0      0 ::1:123                 :::*                               
udp6       0      0 :::123                  :::*             
```


~$ sudo netstat -taup
```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      897/mysqld      
tcp        0      0 localhost:6543          *:*                     LISTEN      894/mythbackend 
tcp        0      0 ******************-C:50724 104.16.112.18:https     ESTABLISHED 2856/firefox    
tcp        0      0 *******************-C:49600 feijoa.canonical.c:http TIME_WAIT   -               
tcp        0      0 ********************-C:36160 151.101.129.69:http     TIME_WAIT   -               
tcp        1      0 ********************-C:60856 productsearch.ubu:https CLOSE_WAIT  3597/unity-scope-ho
tcp6       0      0 ip6-localhost:6543      [::]:*                  LISTEN      894/mythbackend 
udp        0      0 255.255.255.255:1900    *:*                                 894/mythbackend 
udp        0      0 239.255.255.250:1900    *:*                                 894/mythbackend 
udp        0      0 *:bootpc                *:*                                 2184/dhclient   
udp        0      0 *:bootpc                *:*                                 958/dhclient    
udp        0      0 ***********************:ntp *:*                                 1217/ntpd       
udp        0      0 ***********************:ntp *:*                                 1217/ntpd       
udp        0      0 localhost:ntp           *:*                                 1217/ntpd       
udp        0      0 *:ntp                   *:*                                 1217/ntpd       
udp6       0      0 fe80::a243:c901:f5f:ntp [::]:*                              1217/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1217/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1217/ntpd       
udp6       0      0 fd34:1216:9b2:0:35e:ntp [::]:*                              1217/ntpd       
udp6       0      0 fd34:1216:9b2:0:b8f:ntp [::]:*                              1217/ntpd       
udp6       0      0 fe80::e8a5:320f:a75:ntp [::]:*                              1217/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1217/ntpd       
udp6       0      0 2a02:c7d:b5d3:8f00::ntp [::]:*                              1217/ntpd       
udp6       0      0 fd34:1216:9b2:0:526:ntp [::]:*                              1217/ntpd       
udp6       0      0 fd34:1216:9b2:0:ded:ntp [::]:*                              1217/ntpd       
udp6       0      0 ip6-localhost:ntp       [::]:*                              1217/ntpd       
udp6       0      0 [::]:ntp                [::]:*                              1217/ntpd       ]
```


sudo lsof |grep ntp |grep IPv6

```
ntpd      1217             ntp   16u     IPv6              19677      0t0        UDP *:ntp 
ntpd      1217             ntp   20u     IPv6              19688      0t0        UDP ip6-localhost:ntp 
ntpd      1217             ntp   21u     IPv6              19690      0t0        UDP [fd34:1216:9b2:0:ded:f5a7:965f:c132]:ntp 
ntpd      1217             ntp   22u     IPv6              19692      0t0        UDP [fd34:1216:9b2:0:5260:8ca8:229f:2cf5]:ntp 
ntpd      1217             ntp   23u     IPv6              19694      0t0        UDP [2a02:c7d:b5d3:8f00:ded:f5a7:965f:c132]:ntp 
ntpd      1217             ntp   24u     IPv6              19696      0t0        UDP [2a02:c7d:b5d3:8f00:e8b9:c224:465d:3ecc]:ntp 
ntpd      1217             ntp   25u     IPv6              19698      0t0        UDP [fe80::e8a5:320f:a756:bcea]:ntp 
ntpd      1217             ntp   28u     IPv6              27634      0t0        UDP [fd34:1216:9b2:0:b8fc:f1e4:db78:d22f]:ntp 
ntpd      1217             ntp   29u     IPv6              27636      0t0        UDP [fd34:1216:9b2:0:35ec:9651:bc18:9ef8]:ntp 
ntpd      1217             ntp   30u     IPv6              27638      0t0        UDP [2a02:c7d:b5d3:8f00:b8fc:f1e4:db78:d22f]:ntp 
ntpd      1217             ntp   31u     IPv6              27640      0t0        UDP [2a02:c7d:b5d3:8f00:dfe9:4a62:903f:a641]:ntp 
ntpd      1217             ntp   32u     IPv6              27642      0t0        UDP [fe80::a243:c901:f5f6:cabe]:ntp 
```


sudo lsof |grep ntp |grep IPv4

```
ntpd      1217             ntp   17u     IPv4              19680      0t0        UDP *:ntp 
ntpd      1217             ntp   18u     IPv4              19684      0t0        UDP localhost:ntp 
ntpd      1217             ntp   19u     IPv4              19686      0t0        UDP *************************Notebook-PC:ntp 
ntpd      1217             ntp   27u     IPv4              27626      0t0        UDP **************************-Notebook-PC:ntp]
```

---

### Post by TheFu on 2016-06-29
Please edit the post above to use "code tags" (no quotes). Things aren't lining up and are too hard to read.  "Adv Reply" has the # button, but you can just manually swap "quote" for "code" - which is often easier.

A quick scan does show that you have both wifi and wired connected on the same subnet. This is usually less than good. Pick one and use it. turn off/unplug the other.  Need to the routing table - use **route**.  This doesn't have anything to do with the ISP. This is all local networking.

Why are you so worried about ntp?  Enable the firewall to block inbound requests if you are.

---

