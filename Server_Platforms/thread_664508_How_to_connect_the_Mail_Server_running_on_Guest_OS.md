---
title: "How to connect the Mail Server running on Guest OS of VMWare"
date: 2008-01-11
forum: Server Platforms
---

### Post by satimis on 2008-01-11
Hi folks,


How to connect the Mail Server running on Guest OS of VMWare


Ubuntu 7.04 server amd64 (Host OS)
CentOS 5 x86_64 (Guest OS)
VMWare Server
CentOS 5, inet addr - 172.16.103.128


I have only one fixed IP alloted by ISP and one domain. They are used by Ubuntu.  How can I connect the Mail Server/Web server running on CentOS 5?  TIA


B.R.
satimis

---

### Post by rickyjones on 2008-01-11
> **satimis said:**
> Hi folks,


How to connect the Mail Server running on Guest OS of VMWare


Ubuntu 7.04 server amd64 (Host OS)
CentOS 5 x86_64 (Guest OS)
VMWare Server
CentOS 5, inet addr - 172.16.103.128


I have only one fixed IP alloted by ISP and one domain. They are used by Ubuntu.  How can I connect the Mail Server/Web server running on CentOS 5?  TIA


B.R.
satimis

I'm going to say that this will be pretty simple to do but I need you to explain your network layout a bit more.

You say you have one fixed IP allotted to you by your ISP. How is the internet connection configured? Is this server directly connected to the internet (the Ubuntu host I mean) and thus is getting that IP address? Or is your internet connection connected to a router and your host (Ubuntu) and therefore guest (CentOS) are behind the router?

Please include some more information.

Thanks,

-Richard

---

### Post by satimis on 2008-01-11
> **rickyjones said:**
> I'm going to say that this will be pretty simple to do but I need you to explain your network layout a bit more.

You say you have one fixed IP allotted to you by your ISP. How is the internet connection configured? Is this server directly connected to the internet (the Ubuntu host I mean) and thus is getting that IP address? Or is your internet connection connected to a router and your host (Ubuntu) and therefore guest (CentOS) are behind the router?

Please include some more 

Hi Richard,


Network connection;

Server -> Router -> DSL Modem -> Internet

The router is on loan from ISP.  They use it as gateway.  I can't touch it.

Intranet IP address (router ip addr)
Ubuntu - 192.168.0.10
CentOS - 172.16.103.128 ( found with ifconfig)

Only one NIC on the PC


Should you need further info, please inform me.  Thanks


B.R.
saitims

---

### Post by rickyjones on 2008-01-11
Let me confirm that I have this straight.

You have a router from your ISP that you cannot touch. The IP address assigned to your Ubuntu (the actual physical server) is 192.168.0.10. The IP address (dhcp) that is assigned to the Virtual CentOS computer is 172.16.103.128. There are no other computers on this network?

I ask this because I'm not understanding how the Ubuntu server has a private IP of 192.168.xxx.xxx while the CentOS server has something so different by default. Does the CentOS box have internet access with that IP Address?

Do you know if that router is doing NAT? It should be. If so then you'll need access to the router to forward the necessary email ports from the router to your CentOS box. And you'll have to configure the IP on the CentOS box to be on the same network as the rest of your network (the Ubuntu box). 

Is it possible that you have VMWare configured to give your guest a private IP of 172.16.xxx.xxx? If I recall correctly that is also a private IP (but it has been a long time since my IP class...)

Thanks,

-Richard

---

### Post by satimis on 2008-01-11
Hi Richard,


> 
Let me confirm that I have this straight.

You have a router from your ISP that you cannot touch. The IP address assigned to your Ubuntu (the actual physical server) is 192.168.0.10. 

That is correct.


> 
The IP address (dhcp) that is assigned to the Virtual CentOS computer is 172.16.103.128. There are no other computers on this network?

Please let me explain.  I just installed the image of CentOS "CentOS-5_lamp.x86_64.zip"

[http://dev.centos.org/~tru/vmware/centos-5/](http://dev.centos.org/~tru/vmware/centos-5/)

without further configuring it nor its network.


On Ubuntu (Host OS) running;
$ ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:F9:A3:5B  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef9:a35b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3215495 (3.0 MiB)  TX bytes:513664 (501.6 KiB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.59.1  Bcast:172.16.59.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.103.1  Bcast:172.16.103.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```
I found;

```

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.59.1  Bcast:172.16.59.255  Mask:255.255.255.0

```
and
```

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:172.16.59.1  Bcast:172.16.59.255  Mask:255.255.255.0

```
I recall on installing VMWare server it asked whether sharing NIC.  I selected ONE NIC.


> 
I ask this because I'm not understanding how the Ubuntu server has a private IP of 192.168.xxx.xxx while the CentOS server has something so different by default. Does the CentOS box have internet access with that IP Address?

I assigned 191.168.0.10 to Ubuntu.  CentOS can access Internet but NOT vice versa.


> 
Do you know if that router is doing NAT? It should be. If so then you'll need access to the router to forward the necessary email ports from the router to your CentOS box. And you'll have to configure the IP on the CentOS box to be on the same network as the rest of your network (the Ubuntu box). 

I have no info of the router.  I think ISP use it as gateway as well as for remote service to those customer without much knowledge on networking.  ISP told me I can remove their router and can get my own router.  They will give me the password accessing their server.  BUT no further technical assistance will be provided.  I must sign an agreement.


> 
Is it possible that you have VMWare configured to give your guest a private IP of 172.16.xxx.xxx? If I recall correctly that is also a private IP (but it has been a long time since my IP class...)

I also have the same feeling.  But I can't recall exactly.  Please see my reply above.

Thanks


B.R.
satimis

---

### Post by rickyjones on 2008-01-12
alright, this is what I think. I'm fairly certain that the CentOS is assigned a static private IP. You'll need to change this to an IP that can work on your network, just like the host server.

Next you need to access the router, or install your own, and forward the email ports (25) to the CentOS IP.

That should do it!

-Richard

---

### Post by satimis on 2008-01-13
> **rickyjones said:**
> alright, this is what I think. I'm fairly certain that the CentOS is assigned a static private IP. You'll need to change this to an IP that can work on your network, just like the host server.

Next you need to access the router, or install your own, and forward the email ports (25) to the CentOS IP.

That should do it!

Hi Richard,


I found on CentOS

# ifconfig```


eth0      Link encap:Ethernet  HWaddr 00:0C:29:1D:65:AD  
          inet addr:172.16.103.128  Bcast:172.16.103.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe1d:65ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9632 (9.4 KiB)  TX bytes:15868 (15.4 KiB)
          Base address:0x1070 Memory:ec820000-ec840000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19072 (18.6 KiB)  TX bytes:19072 (18.6 KiB)

```
I suppose "inet addr:172.16.103.128" is the fixed IP of CentOS.


How can I make use of iptables to forward port 25, 80, 443 etc. to it?


On Ubuntu
$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d 220.232.213.178 --reject-with icmp-port-unreachable

# allows squirrelmail input
#iptables -I INPUT 7 -p ALL -i lo --source 127.0.0.1 -j ACCEPT

#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s 220.232.213.178 -p UDP --destination-port 53

# reject all other traffic from localhost
#iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 3 -j REJECT -s 220.232.213.178 --reject-with icmp-port-unreachable

```
I'll keep my hands off the router loaded by ISP.  Neither I'll consider replacing it with my own unless there is no alternative solution because of the agreement.


On another thought if forwarding all ports to CentOS then how can the server on Ubuntu work.  Can I use Ubuntu as Mail Server and CentOS as webserver?


B.R.
satimis

---

### Post by rickyjones on 2008-01-13
> **satimis said:**
> Hi Richard,


I found on CentOS

# ifconfig```


eth0      Link encap:Ethernet  HWaddr 00:0C:29:1D:65:AD  
          inet addr:172.16.103.128  Bcast:172.16.103.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe1d:65ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9632 (9.4 KiB)  TX bytes:15868 (15.4 KiB)
          Base address:0x1070 Memory:ec820000-ec840000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19072 (18.6 KiB)  TX bytes:19072 (18.6 KiB)

```
I suppose "inet addr:172.16.103.128" is the fixed IP of CentOS.


How can I make use of iptables to forward port 25, 80, 443 etc. to it?


On Ubuntu
$ cat /etc/rc.local```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#exit 0

#
# INPUT
#

# allow all incoming traffic from the management interface NIC
# as long as it is a part of an established connection
iptables -I INPUT 1 -j ACCEPT -d 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all ssh traffic to the management interface NIC
iptables -I INPUT 2 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 22

# allow all VMware MUI HTTP traffic to the management interface NIC
iptables -I INPUT 3 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8222

# allow all VMware MUI HTTPS traffic to the management interface NIC
iptables -I INPUT 4 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 8333

# allow all VMware Authorization Daemon traffic to the management interface NIC
iptables -I INPUT 5 -j ACCEPT -p TCP -d 220.232.213.178 --destination-port 902

# reject all other traffic to the management interface NIC
iptables -I INPUT 6 -j REJECT -d 220.232.213.178 --reject-with icmp-port-unreachable

# allows squirrelmail input
#iptables -I INPUT 7 -p ALL -i lo --source 127.0.0.1 -j ACCEPT

#
# OUTPUT
#

# allow all outgoing traffic from the management interface NIC
# if it is a part of an established connection
iptables -I OUTPUT 1 -j ACCEPT -s 220.232.213.178 -m state --state RELATED,ESTABLISHED

# allow all DNS queries from the management interface NIC
iptables -I OUTPUT 2 -j ACCEPT -s 220.232.213.178 -p UDP --destination-port 53

# reject all other traffic from localhost
#iptables -I OUTPUT 3 -j REJECT -s 127.0.0.1 --reject-with icmp-port-unreachable

# reject all other traffic from the management interface NIC
iptables -I OUTPUT 3 -j REJECT -s 220.232.213.178 --reject-with icmp-port-unreachable

```
I'll keep my hands off the router loaded by ISP.  Neither I'll consider replacing it with my own unless there is no alternative solution because of the agreement.


On another thought if forwarding all ports to CentOS then how can the server on Ubuntu work.  Can I use Ubuntu as Mail Server and CentOS as webserver?


B.R.
satimis

Well, you need the CentOS server to be on the same network as the Ubuntu server. Basically if you plug another computer into your network you should be able to ping both servers successfully and both server should be able to access the internet without issue. 

Forwarding the ports from the Ubuntu server to the CentOS server will do nothing for you in this case because you need to forward the ports from your router to the CentOS server.

You can have as many different servers on your network as you'd want. You just have to make sure that the router forwards the correct ports to the correct server and that they can communicate without issue.

I hope this helps!

-Richard

---

### Post by satimis on 2008-01-14
> **rickyjones said:**
> Well, you need the CentOS server to be on the same network as the Ubuntu server. Basically if you plug another computer into your network you should be able to ping both servers successfully and both server should be able to access the internet without issue. 
That is correct.  Ping CentOS ip address.


$ ping -c3 172.16.103.128```

PING 172.16.103.128 (172.16.103.128) 56(84) bytes of data.
64 bytes from 172.16.103.128: icmp_seq=1 ttl=64 time=0.933 ms
64 bytes from 172.16.103.128: icmp_seq=2 ttl=64 time=0.149 ms
64 bytes from 172.16.103.128: icmp_seq=3 ttl=64 time=0.156 ms

--- 172.16.103.128 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.149/0.412/0.933/0.368 ms

```


> 
Forwarding the ports from the Ubuntu server to the CentOS server will do nothing for you in this case because you need to forward the ports from your router to the CentOS server.

You can have as many different servers on your network as you'd want. You just have to make sure that the router forwards the correct ports to the correct server and that they can communicate without issue.

Performed following test w/o success

1)
On Ubuntu

connect CentOS
$ ssh 172.16.103.128
satimis@172.16.103.128's password:
$ su -
Password:

# ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:0C:29:1D:65:AD  
          inet addr:172.16.103.128  Bcast:172.16.103.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe1d:65ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10046 (9.8 KiB)  TX bytes:16808 (16.4 KiB)
          Base address:0x1070 Memory:ec820000-ec840000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

```

# ifconfig eth0:0 192.168.0.20
No complaint

# ifconfig```

eth0      Link encap:Ethernet  HWaddr 00:0C:29:1D:65:AD  
          inet addr:172.16.103.128  Bcast:172.16.103.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe1d:65ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:447 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256458 (250.4 KiB)  TX bytes:70495 (68.8 KiB)
          Base address:0x1070 Memory:ec820000-ec840000 

eth0:0    Link encap:Ethernet  HWaddr 00:0C:29:1D:65:AD  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Base address:0x1070 Memory:ec820000-ec840000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:560 (560.0 b)  TX bytes:560 (560.0 b)

```


# /etc/init.d/network restart```

Shutting down interface eth0:                              [  OK  ]
Shutting down loopback interface:                          [  OK  ]
Bringing up loopback interface:                            [  OK  ]
Bringing up interface eth0:  
Determining IP information for eth0... done.
                                                           [  OK  ]

```


# /etc/init.d/httpd start```

Starting httpd:                                            [  OK  ]

```


Called ISP requesting to make following change;

forward port 8080 to IP addr 192.168.0.20


On Ubuntu
$ sudo /etc/init.d/apache2 stop```

 * Stopping web server (apache2)...                                      [ OK ] 
```


On Firefox;
running:-
[http://www.satimis.com](http://www.satimis.com)
[http://www.satimis.com:8080](http://www.satimis.com:8080) (just hanging)
[http://www.satimis.com/8080](http://www.satimis.com/8080)

[https://www.satimis.com](https://www.satimis.com)
[https://www.satimis.com:8080](https://www.satimis.com:8080) (just hanging)
[https://www.satimis.com/8080](https://www.satimis.com/8080)

All failed.


2)
On CentOS Firefox running;
localhost

start ```

Apache 2 Test Page
powered by CentOS

```


Any advice?  TIA


B.R.
satimis

---

### Post by rickyjones on 2008-01-14
I tried the first link and it took me to a server.
```

Apache/2.2.3 (Ubuntu) DAV/2 SVN/1.4.3 PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at www.satimis.com Port 80

```

The port 8080 one is not working. An NMAP scan of [www.satimis.com](www.satimis.com) comes up with the following:
```

C:\Documents and Settings\richard>nmap -sS -A -v -P0 www.satimis.com

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-14 11:57 Eastern Standard
Time
Initiating Parallel DNS resolution of 1 host. at 11:57
Completed Parallel DNS resolution of 1 host. at 11:57, 0.55s elapsed
Initiating SYN Stealth Scan at 11:57
Scanning 220.232.213.178 [1697 ports]
Discovered open port 80/tcp on 220.232.213.178
Discovered open port 25/tcp on 220.232.213.178
Discovered open port 443/tcp on 220.232.213.178
Discovered open port 110/tcp on 220.232.213.178
Discovered open port 1080/tcp on 220.232.213.178
Discovered open port 143/tcp on 220.232.213.178
Discovered open port 10000/tcp on 220.232.213.178
Discovered open port 995/tcp on 220.232.213.178
Completed SYN Stealth Scan at 11:57, 25.50s elapsed (1697 total ports)
Initiating Service scan at 11:57
Scanning 8 services on 220.232.213.178
Completed Service scan at 11:58, 23.23s elapsed (8 services on 1 host)
Initiating OS detection (try #1) against 220.232.213.178
Retrying OS detection (try #2) against 220.232.213.178
Initiating gen1 OS Detection against 220.232.213.178 at 59.141s
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
Insufficient responses for TCP sequencing (0), OS detection may be less accurate

For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
Insufficient responses for TCP sequencing (0), OS detection may be less accurate

Host 220.232.213.178 appears to be up ... good.
Interesting ports on 220.232.213.178:
Not shown: 1683 closed ports
PORT      STATE    SERVICE      VERSION
25/tcp    open     smtp         Postfix smtpd
80/tcp    open     http         Apache httpd 2.2.3 ((Ubuntu) DAV/2 SVN/1.4.3 PHP
/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c)
110/tcp   open     pop3-proxy   AVG pop3 proxy 7.5.510/7.5.516
135/tcp   filtered msrpc
137/tcp   filtered netbios-ns
138/tcp   filtered netbios-dgm
139/tcp   filtered netbios-ssn
143/tcp   open     imap         Courier Imapd (released 2005)
443/tcp   open     ssl          OpenSSL
445/tcp   filtered microsoft-ds
995/tcp   open     ssl          OpenSSL
1080/tcp  open     tcpwrapped
8080/tcp  filtered http-proxy
10000/tcp open     http         Webmin httpd
Device type: router|general purpose|printer|bridge|broadband router
Running (JUST GUESSING) : Cisco IOS 12.X (93%), Sun Solaris 8 (93%), Canon embed
ded (90%), Linux 2.6.X|2.4.X (90%), Microsoft Windows NT/2K/XP|2003/.NET (90%),
RiverStone embedded (90%), Cisco embedded (87%), Linksys embedded (87%)
Aggressive OS guesses: Cisco 2611 router running IOS 12.0(7)T (93%), Sun Solaris
 8 (93%), Canon iR 2200 printer (90%), Linux 2.6.8 - 2.6.9 (90%), Microsoft Wind
ows 2000 Server SP4 or 2003 Server Standard Edition (90%), RiverStone RS3000 rou
ter (90%), Cisco Accesspoint 1200 (87%), Linksys WRT54G Wireless Broadband Route
r (Linux kernel 2.4.20) (87%), Linux 2.4.9 - 2.4.18 (87%), Linux 2.6.11 (87%)
No exact OS matches for host (test conditions non-ideal).
Service Info: Host:  mail.satimis.com; OS: Windows

OS and Service detection performed. Please report any incorrect results at http:
//insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 109.266 seconds
               Raw packets sent: 1849 (87.172KB) | Rcvd: 1842 (75.604KB)

```
It looks like 8080 is in a filtered state which leads me to believe that the router is either having issues forwarding it or else the router cannot contact the server correctly.

Hope it helps!

-Richard

---

### Post by satimis on 2008-01-17
> **rickyjones said:**
> I tried the first link and it took me to a server.
```

Apache/2.2.3 (Ubuntu) DAV/2 SVN/1.4.3 PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at www.satimis.com Port 80

```

The port 8080 one is not working. An NMAP scan of [www.satimis.com](www.satimis.com) comes up with the following:
```

C:\Documents and Settings\richard>nmap -sS -A -v -P0 www.satimis.com

Starting Nmap 4.20 ( http://insecure.org ) at 2008-01-14 11:57 Eastern Standard
Time
Initiating Parallel DNS resolution of 1 host. at 11:57
Completed Parallel DNS resolution of 1 host. at 11:57, 0.55s elapsed
Initiating SYN Stealth Scan at 11:57
Scanning 220.232.213.178 [1697 ports]
Discovered open port 80/tcp on 220.232.213.178
Discovered open port 25/tcp on 220.232.213.178
Discovered open port 443/tcp on 220.232.213.178
Discovered open port 110/tcp on 220.232.213.178
Discovered open port 1080/tcp on 220.232.213.178
Discovered open port 143/tcp on 220.232.213.178
Discovered open port 10000/tcp on 220.232.213.178
Discovered open port 995/tcp on 220.232.213.178
Completed SYN Stealth Scan at 11:57, 25.50s elapsed (1697 total ports)
Initiating Service scan at 11:57
Scanning 8 services on 220.232.213.178
Completed Service scan at 11:58, 23.23s elapsed (8 services on 1 host)
Initiating OS detection (try #1) against 220.232.213.178
Retrying OS detection (try #2) against 220.232.213.178
Initiating gen1 OS Detection against 220.232.213.178 at 59.141s
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
Insufficient responses for TCP sequencing (0), OS detection may be less accurate

For OSScan assuming port 25 is open, 1 is closed, and neither are firewalled
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
WARNING:  RST from port 25 -- is this port really open?
Insufficient responses for TCP sequencing (0), OS detection may be less accurate

Host 220.232.213.178 appears to be up ... good.
Interesting ports on 220.232.213.178:
Not shown: 1683 closed ports
PORT      STATE    SERVICE      VERSION
25/tcp    open     smtp         Postfix smtpd
80/tcp    open     http         Apache httpd 2.2.3 ((Ubuntu) DAV/2 SVN/1.4.3 PHP
/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c)
110/tcp   open     pop3-proxy   AVG pop3 proxy 7.5.510/7.5.516
135/tcp   filtered msrpc
137/tcp   filtered netbios-ns
138/tcp   filtered netbios-dgm
139/tcp   filtered netbios-ssn
143/tcp   open     imap         Courier Imapd (released 2005)
443/tcp   open     ssl          OpenSSL
445/tcp   filtered microsoft-ds
995/tcp   open     ssl          OpenSSL
1080/tcp  open     tcpwrapped
8080/tcp  filtered http-proxy
10000/tcp open     http         Webmin httpd
Device type: router|general purpose|printer|bridge|broadband router
Running (JUST GUESSING) : Cisco IOS 12.X (93%), Sun Solaris 8 (93%), Canon embed
ded (90%), Linux 2.6.X|2.4.X (90%), Microsoft Windows NT/2K/XP|2003/.NET (90%),
RiverStone embedded (90%), Cisco embedded (87%), Linksys embedded (87%)
Aggressive OS guesses: Cisco 2611 router running IOS 12.0(7)T (93%), Sun Solaris
 8 (93%), Canon iR 2200 printer (90%), Linux 2.6.8 - 2.6.9 (90%), Microsoft Wind
ows 2000 Server SP4 or 2003 Server Standard Edition (90%), RiverStone RS3000 rou
ter (90%), Cisco Accesspoint 1200 (87%), Linksys WRT54G Wireless Broadband Route
r (Linux kernel 2.4.20) (87%), Linux 2.4.9 - 2.4.18 (87%), Linux 2.6.11 (87%)
No exact OS matches for host (test conditions non-ideal).
Service Info: Host:  mail.satimis.com; OS: Windows

OS and Service detection performed. Please report any incorrect results at http:
//insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 109.266 seconds
               Raw packets sent: 1849 (87.172KB) | Rcvd: 1842 (75.604KB)

```
It looks like 8080 is in a filtered state which leads me to believe that the router is either having issues forwarding it or else the router cannot contact the server correctly.

Hi Richard,


I'm still googling around for a solution.  I don't think my problem is solely on account of port forwarding.  I believe the problem is due to misconfiguration.

Port 8080 is now forwarded to 192.168.0.20, the IP addr of CentOS - Guest OS.  It was done by ISP upon my request who owns the router.  It have been confirmed with ISP twice.


I found following thread;
Bridge  on Posting  # 3
[http://ubuntuforums.org/showthread.php?t=617225](http://ubuntuforums.org/showthread.php?t=617225)
November 19th, 2007
bodhi.zazen's Avatar 


The case is similar to mine, except the guest OS being OpenVZ.  I haven't figured out what shall I replaced "101" on setting up the Guest connection.  I posted on;

Posting #11	satimis
[http://ubuntuforums.org/showthread.php?t=617225&page=2](http://ubuntuforums.org/showthread.php?t=617225&page=2)

I'm now waiting a response.  I'll update the situation if any?


satimis

---

