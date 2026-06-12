---
title: "Multi Homed IP with Multiple NICs - One IP doesn't respond"
date: 2009-12-15
forum: Server Platforms
---

### Post by DantePasquale on 2009-12-15
Hi,

I upgraded from 9.04 to 9.10 and am down to one remaining problem, and its really, really weird.

I have 2 NICs in my server and have multiple IPs on both NICs. All are on the same vlan.

According to wireshark & tcpdump, there's absolutely no IP traffic on NIC1, all is on NIC0, even to IPs plumbed on NIC1!! 

**QUESTION**: Is this because ALL outbound traffic is on eth0, so arp assigns the MAC of eth0 for ALL IPs on this server?


Another symptom: I pointed NS server entry in Registry.Com for one of my domains to the ns1 IP and it never responds to DNS requests -- external to VLAN. I changed registry.com to point to another IP, on the same NIC, and it works properly!

Here's my /etc/network/interfaces file:

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 74.1.46.162
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160
gateway 74.1.46.161

iface eth0:1 inet static
address 74.1.46.163
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth0:2 inet static
address 74.1.46.164
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth0:3 inet static
address 74.1.46.165
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth1 inet static
address 74.1.46.166
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth1:1 inet static
address 74.1.46.167
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth1:2 inet static
address 74.1.46.168
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth1:3 inet static
address 74.1.46.169
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160

iface eth1:4 inet static
address 74.1.46.174
netmask 255.255.255.240
broadcast 74.1.46.175
network 74.1.46.160


auto eth0
auto eth0:1
auto eth0:2
auto eth0:3
auto eth1
auto eth1:1
auto eth1:2
auto eth1:3
auto eth1:4

```

Here's ifconfig -a:

```
eth0      Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4
          inet addr:74.1.46.162  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:266332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21288994 (21.2 MB)  TX bytes:47334848 (47.3 MB)
          Interrupt:30 Base address:0xe000

eth0:1    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4
          inet addr:74.1.46.163  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:30 Base address:0xe000

eth0:2    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4
          inet addr:74.1.46.164  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:30 Base address:0xe000

eth0:3    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a4
          inet addr:74.1.46.165  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:30 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5
          inet addr:74.1.46.166  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1900882 (1.9 MB)  TX bytes:6798 (6.7 KB)
          Interrupt:31

eth1:1    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5
          inet addr:74.1.46.167  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:31

eth1:2    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5
          inet addr:74.1.46.168  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:31

eth1:3    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5
          inet addr:74.1.46.169  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:31

eth1:4    Link encap:Ethernet  HWaddr 00:e0:81:72:ed:a5
          inet addr:74.1.46.174  Bcast:74.1.46.175  Mask:255.255.255.240
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:31

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8216190 (8.2 MB)  TX bytes:8216190 (8.2 MB)
```

Here's netstat -tap

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 inferno.cocoanet.u:7634 *:*                     LISTEN      3573/hddtemp
tcp        0      0 *:ftp                   *:*                     LISTEN      3769/pure-ftpd (SER
tcp        0      0 h-74-1-46-174.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-169.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-168.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-167.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-166.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-165.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 h-74-1-46-164.sf:domain *:*                     LISTEN      3593/mydns
tcp        0      0 www.cocoanet.us:domain  *:*                     LISTEN      3593/mydns
tcp        0      0 inferno.cocoanet:domain *:*                     LISTEN      3593/mydns
tcp        0      0 inferno.cocoanet:domain *:*                     LISTEN      3593/mydns
tcp        0      0 *:ssh                   *:*                     LISTEN      2323/sshd
tcp        0      0 *:ipp                   *:*                     LISTEN      3994/cupsd
tcp        0      0 *:smtp                  *:*                     LISTEN      3730/master
tcp        0      0 inferno.cocoanet.u:5433 *:*                     LISTEN      2779/postgres
tcp        0      0 inferno.cocoanet.u:6010 *:*                     LISTEN      19060/0
tcp        0      0 *:8443                  *:*                     LISTEN      4230/apache2
tcp        0      0 *:https                 *:*                     LISTEN      4230/apache2
tcp        0      0 *:microsoft-ds          *:*                     LISTEN      3817/smbd
tcp        0      0 h-74-1-46-:microsoft-ds 109.122.192.21:3448     SYN_RECV    -
tcp        0      0 *:imaps                 *:*                     LISTEN      3342/couriertcpd
tcp        0      0 *:pop3s                 *:*                     LISTEN      3390/couriertcpd
tcp        0      0 inferno.cocoanet.:10024 *:*                     LISTEN      2470/amavisd (maste
tcp        0      0 inferno.cocoanet.:10025 *:*                     LISTEN      3730/master
tcp        0      0 *:mysql                 *:*                     LISTEN      2663/mysqld
tcp        0      0 *:netbios-ssn           *:*                     LISTEN      3817/smbd
tcp        0      0 *:pop3                  *:*                     LISTEN      3363/couriertcpd
tcp        0      0 *:imap2                 *:*                     LISTEN      3315/couriertcpd
tcp        0      0 inferno.cocoanet.:spamd *:*                     LISTEN      2877/spamd.pid
tcp        0      0 *:www                   *:*                     LISTEN      4230/apache2
tcp        0      0 *:5552                  *:*                     LISTEN      2364/tprintdaemon
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:48456 ESTABLISHED 4956/couriertls
tcp        0      0 www.cocoanet.us:www     207.46.55.29:42596      FIN_WAIT2   -
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:41280 ESTABLISHED 18880/couriertls
tcp        0      0 inferno.cocoanet.:43918 inferno.cocoanet.:mysql ESTABLISHED 18652/amavisd (ch3-
tcp        0      0 h-74-1-46-166.sfl:imaps h-74-1-46-173.sfl:52528 ESTABLISHED 4998/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:48469 ESTABLISHED 4997/couriertls
tcp        0      0 h-74-1-46-166.sfl:imaps h-74-1-46-173.sfl:60167 ESTABLISHED 18213/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:50734 ESTABLISHED 18515/couriertls
tcp        1  11264 www.cocoanet.us:www     proxy.palmers.ac.:56663 CLOSE_WAIT  4275/apache2
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:48466 ESTABLISHED 4994/couriertls
tcp        0      0 inferno.cocoanet.:mysql inferno.cocoanet.:43906 ESTABLISHED 2663/mysqld
tcp        0      0 inferno.cocoanet.u:6010 inferno.cocoanet.:60201 TIME_WAIT   -
tcp        0      0 h-74-1-46-166.sfl:imaps h-74-1-46-173.sfl:52525 ESTABLISHED 4995/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:44616 ESTABLISHED 18084/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:48465 ESTABLISHED 4993/couriertls
tcp        0      0 h-74-1-46-166.sfl:imaps h-74-1-46-173.sfl:52526 ESTABLISHED 4996/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:54620 ESTABLISHED 18383/couriertls
tcp        0      0 inferno.cocoanet.:43906 inferno.cocoanet.:mysql ESTABLISHED 18398/amavisd (ch3-
tcp        0      0 inferno.cocoanet.:mysql inferno.cocoanet.:43918 ESTABLISHED 2663/mysqld
tcp        0      0 h-74-1-46-166.sfl:imaps h-74-1-46-173.sfl:52530 ESTABLISHED 5003/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:40321 ESTABLISHED 18717/couriertls
tcp        0      0 www.cocoanet.us:imaps   h-74-1-46-173.sfl:48471 ESTABLISHED 5000/couriertls

```
Here's netstat -rn
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
74.1.46.160     0.0.0.0         255.255.255.240 U         0 0          0 eth0
74.1.46.160     0.0.0.0         255.255.255.240 U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         74.1.46.161     0.0.0.0         UG        0 0          0 eth0

```

Here's iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
fail2ban-ssh  tcp  --  anywhere             anywhere            multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain fail2ban-ssh (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere

```

This was working as expected on 9.04.

NOTE: I had to disable ipv6 in kernel to keep mydns from puking, but had this problem regardless.

---

### Post by BkkBonanza on 2009-12-15
What does output from "ip route" give you?

It looks like both your interfaces have overlapping subnet spaces. I'm not sure that's a problem but does seem like it could be. Maybe try eth1 with a different netmask so it doesn't overlap eth0 - just wondering.

Edit: Oops. Sorry - just saw that you already posted routing info.

I think your problem is that those overlapping subnets will cause traffic for any IP to be routed via the first route matching, which is eth0.

---

### Post by DantePasquale on 2009-12-15
Thanks ... I agree that outbound traffic will always go out eth0 according to the route table -- grabs the first available NIC for a given route.

I'm more confused about INBOUND connections. Why would ALL traffic that is inbound go to eth0, even IP traffic bound for an IP on eth1 ??? 

How does that even work? 

Let's say I have an IP connection to 74.1.46.174 which is eth1:4. But the packets all come in via eth0. How does this get to the application listening on eth1???? 

I really don't get this :(

---

### Post by BkkBonanza on 2009-12-15
I'm not sure how this works. I did use two NICs once but my config had a iptables rule that tagged traffic to route them evenly between the two interfaces. I know that once a connection was started on one route it always stayed on that route.

Is the application actually accepting a connection and receiving data on 74.1.46.174?

---

### Post by DantePasquale on 2009-12-15
Looks to me like Apache Virtualhosts are configured to listen on ALL Ip's:

```
<VirtualHost *:80>
      DocumentRoot /var/www/cocoanet.us/web

    ServerName cocoanet.us
    ServerAlias *.cocoanet.us

```

mydns is also listening on ALL ip addresses. Guess that's why its working. I'll have to figure out how to use both nics for outbound (at least).

But that gets me more confused on why pointing register.com to 74.1.46.168 didn't work -- no traffic at all; but changing register.com to point to 74.1.46.167 did work!!! I'm getting a headache and maybe being to nitpicky, but I'd really like to know how this works;)

Thanks!

---

### Post by BkkBonanza on 2009-12-15
If you want to balance your outboound traffic over two nics then you may find my script below useful. Of course, you'd have to modify it. I wish I had a reference to the web site where I learned how to set this up but I don't any more.

Anyway, in the last line is a weight value for each route that determines how to balance the connections going out. My two gateways going out were 192.168.1.1 and 192.168.0.10. 

Hope this helps somewhat. It did work for me.

```
#!/bin/bash

eth1=`ifconfig  | grep 'inet addr:192.168.1'| grep -v '127.0.0.1' | cut -d: -f2 | awk '{ print $1}'`;
echo 'Routing for '$eth1

sudo ifconfig eth0 192.168.0.103

sudo ip route replace 192.168.0.0/24 dev eth0 src 192.168.0.103 table T1
sudo ip route replace default via 192.168.0.10 table T1
sudo ip route replace 127.0.0.0/8 dev lo table T1

sudo ip route replace 192.168.1.0/24 dev eth1 src $eth1 table T2
sudo ip route replace default via 192.168.1.1 table T2
sudo ip route replace 127.0.0.0/8 dev lo table T2

sudo ip rule add from 192.168.0.103 table T1
sudo ip rule add from $eth1 table T2

sudo ip route replace 192.168.0.0/24 dev eth0 src 192.168.0.103
sudo ip route replace 192.168.1.0/24 dev eth1 src $eth1

sudo ip route replace default scope global nexthop via 192.168.0.10 dev eth0 weight 1 nexthop via 192.168.1.1 dev eth1 weight 1


```

Note - the $eth1 variable is set on the fly because that connection used dhcp and the ip assigned could change. The eth0 ip value was static so I had it coded in.

You could probably adjust the rules so that the nic used outbound depends on the source rather than weight value. More research required.

---

