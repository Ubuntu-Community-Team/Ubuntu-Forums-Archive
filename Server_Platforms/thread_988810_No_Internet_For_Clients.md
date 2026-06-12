---
title: "No Internet For Clients"
date: 2008-11-20
forum: Server Platforms
---

### Post by shoaibi on 2008-11-20
I am trying to setup a complete ubuntu gateway. I have Ubuntu 8.04 LTS Server installed with dhcp3-server, bind9 and dnsutils.

Following shows my configuration as well as the problem:


Ext_IP <=> (10.0.0.138) DSL Routher -DHCP/DNS- (NAT) <=> eth0 <=> (10.0.0.3) Server -DHCP/DNS- <=> eth1 (172.20.0.1) <=> switch <=> clients



Server:
hostname= nextcube
eth0: External IP NATted on 10.0.0.3
eth1: Internel IP interface, 172.20.0.1


/etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
   address 172.20.0.1
   netmask 255.255.255.0
   broadcast 172.20.0.255
   gateway 10.0.0.138
# even tried with gateway equal to 10.0.0.3 or 172.20.0.1 as well

```

/etc/hosts:
```

127.0.0.1	localhost
127.0.1.1	nextcube.cosp.hq nextcube ns1 ns1.cosp.hq

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


DHCP Server Config:
```

# option definitions common to all supported networks...
option domain-name "cosp.hq";
option domain-name-servers ns1.cosp.hq; # ns1.cosp.hq is 127.0.1.1

default-lease-time 600;
max-lease-time 7200;

subnet 172.20.0.0 netmask 255.255.255.0 {
  range 172.20.0.100 172.20.0.200;
  option domain-name-servers ns1.cosp.hq;
  option domain-name "cosp.hq";
  option routers 10.0.0.138;
  option broadcast-address 172.20.0.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```



DNS Server Config:
```

root@nextcube:/etc/bind# cat named.conf
named.conf          named.conf.local    named.conf.options  
root@nextcube:/etc/bind# cat named.conf.local 
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "cosp.hq" {
type master;
file "/etc/bind/zones/cosp.hq.db";
};

zone "0.20.172.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.0.20.172.in-addr.arpa";
};
root@nextcube:/etc/bind# cat named.conf.options 
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you might need to uncomment the query-source
	// directive below.  Previous versions of BIND always asked
	// questions using port 53, but BIND 8.1 and later use an unprivileged
	// port by default.

	// query-source address * port 53;


	 forwarders {
                #OpenDNS Ones
	 	208.67.222.222;
                208.67.220.220;
               
                #ISP ones

	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

root@nextcube:/etc/bind# cat zones/cosp.hq.db 
cosp.hq. IN SOA ns1.cosp.hq. admin.cosp.hq. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)

// Replace the following line as necessary:
ns1 = DNS Server name
// mail = mail server name
cosp.hq = domain name
cosp.hq. IN NS ns1.cosp.hq.
//cosp.hq. IN MX 10 mail.cosp.hq.

// Replace the IP address with the right IP addresses.
www IN A 172.20.0.1
//mta IN A 192.168.0.3
ns1 IN A 172.20.0.1
root@nextcube:/etc/bind# cat zones/rev.0.20.172.in-addr.arpa 
@ IN SOA ns1.cosp.hq. admin.cosp.hq. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS ns1.cosp.hq.
1 IN PTR cosp.hq

```






Firewall Rules:
```

root@nextcube:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.20.0.0/24        anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```




on Server:
```

root@nextcube:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:c7:49:d7:97  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:c7ff:fe49:d797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44388 (43.3 KB)  TX bytes:19449 (18.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:06:22:90  
          inet addr:172.20.0.1  Bcast:172.20.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe06:2290/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:240041 (234.4 KB)  TX bytes:483520 (472.1 KB)
          Interrupt:21 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10605 (10.3 KB)  TX bytes:10605 (10.3 KB)

root@nextcube:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     0      0        0 eth0
172.20.0.0      *               255.255.255.0   U     0      0        0 eth1
default         10.0.0.138      0.0.0.0         UG    100    0        0 eth0
root@nextcube:~# ping google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=239 time=326 ms

--- google.com ping statistics ---
2 packets transmitted, 1 received, 50% packet loss, time 999ms
rtt min/avg/max/mdev = 326.696/326.696/326.696/0.000 ms
root@nextcube:~# ping 172.20.0.101
PING 172.20.0.101 (172.20.0.101) 56(84) bytes of data.
64 bytes from 172.20.0.101: icmp_seq=1 ttl=64 time=0.423 ms
64 bytes from 172.20.0.101: icmp_seq=2 ttl=64 time=0.373 ms

--- 172.20.0.101 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.373/0.398/0.423/0.025 ms

root@nextcube:/etc/bind# cat /etc/resolv.conf 
search cosp.hq
nameserver 172.20.0.1
root@nextcube:/etc/bind# dig google.com

; <<>> DiG 9.4.2-P2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 35599
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 13, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		217	IN	A	72.14.207.99
google.com.		217	IN	A	64.233.187.99
google.com.		217	IN	A	209.85.171.99

;; AUTHORITY SECTION:
.			515646	IN	NS	A.ROOT-SERVERS.NET.
.			515646	IN	NS	I.ROOT-SERVERS.NET.
.			515646	IN	NS	B.ROOT-SERVERS.NET.
.			515646	IN	NS	M.ROOT-SERVERS.NET.
.			515646	IN	NS	L.ROOT-SERVERS.NET.
.			515646	IN	NS	C.ROOT-SERVERS.NET.
.			515646	IN	NS	G.ROOT-SERVERS.NET.
.			515646	IN	NS	J.ROOT-SERVERS.NET.
.			515646	IN	NS	H.ROOT-SERVERS.NET.
.			515646	IN	NS	D.ROOT-SERVERS.NET.
.			515646	IN	NS	K.ROOT-SERVERS.NET.
.			515646	IN	NS	F.ROOT-SERVERS.NET.
.			515646	IN	NS	E.ROOT-SERVERS.NET.

;; Query time: 349 msec
;; SERVER: 172.20.0.1#53(172.20.0.1)
;; WHEN: Fri Nov 21 07:55:27 2008
;; MSG SIZE  rcvd: 287

```



On Client:

```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:6e:e4:ce  
          inet addr:172.20.0.101  Bcast:172.20.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe6e:e4ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1017 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:119720 (119.7 KB)  TX bytes:121429 (121.4 KB)
          Memory:e4600000-e4620000 

$ ping 172.20.0.1
PING 172.20.0.1 (172.20.0.1) 56(84) bytes of data.
64 bytes from 172.20.0.1: icmp_seq=1 ttl=64 time=0.906 ms
64 bytes from 172.20.0.1: icmp_seq=2 ttl=64 time=0.308 ms
64 bytes from 172.20.0.1: icmp_seq=3 ttl=64 time=0.288 ms
^C
--- 172.20.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2008ms
rtt min/avg/max/mdev = 0.288/0.500/0.906/0.287 ms

$ ping google.com
ping: unknown host google.com

$ ping nextcube
ping: unknown host nextcube

$ ping 202.67.222.222
connect: Network is unreachable

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.240.0    *               255.255.255.0   U     0      0        0 vmnet8
172.20.0.0      *               255.255.255.0   U     0      0        0 eth0
192.168.191.0   *               255.255.255.0   U     0      0        0 vmnet1

```


Even tried to disable DHCP and DNS on DSL router and assign it 172.20.0.254 and eth0=172.20.0.1 while eth1=172.20.0.2, and setting the gateway option as 172.20.0.254 in dhcp config, didn't worked...

---

### Post by doas777 on 2008-11-20
well one thing, if you are forwarding DNS queries, you need to open UDP 53 inbound on the firewall. remember, UDP does not have "connections" so the DNS response will look like an unsolicited packet, and be dropped. check your logs for dropped packets.

also your missing a default route (0.0.0.0/0) in your route table, and I think you may be using the vmnet interfaces strangley. you may wanna look at that. 


good luck,
franklin

---

### Post by shoaibi on 2008-11-20
For DNS i did rather a general thing:
```

root@nextcube:~# iptables -A INPUT -i eth1 -s 172.20.0/24 -j ACCEPT
root@nextcube:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.20.0.0/24        anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.20.0.0/24        anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

e.g. Allowing everything from local network for the time being....

couldn't understand about that 0.0.0.0/0 route...

---

### Post by doas777 on 2008-11-20
> **shoaibi said:**
> For DNS i did rather a general thing:
```

root@nextcube:~# iptables -A INPUT -i eth1 -s 172.20.0/24 -j ACCEPT
root@nextcube:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.20.0.0/24        anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  172.20.0.0/24        anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

e.g. Allowing everything from local network for the time being....

couldn't understand about that 0.0.0.0/0 route...

but is the server accepting the response from the forwarder?

in terms of the 0.0.0.0/0, it is the default gateway, and should point out your wan interface ( vmlan8 ) and point to your network gateway. right now your router knows 3 networks, so if you request a network that is not one of those, your router needs to know what to do with it (eg route it to a the next hop gateway).

here is my route table. not the route "DEFAULT":
```

alpha10@21of2:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.77.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.77.1    0.0.0.0         UG    100    0        0 eth0

```

---

### Post by shoaibi on 2008-11-21
May be this will help:

On Client:
```

root@abacus:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.240.0    *               255.255.255.0   U     0      0        0 vmnet8
172.20.0.0      *               255.255.255.0   U     0      0        0 eth0
192.168.191.0   *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 eth0
root@abacus:~# route add default 10.0.0.138
SIOCADDRT: No such device
root@abacus:~# route add default 172.20.0.1
SIOCADDRT: No such device
root@abacus:~# ping google.com
ping: unknown host google.com
root@abacus:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:6e:e4:ce  
          inet addr:172.20.0.101  Bcast:172.20.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe6e:e4ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13582 (13.5 KB)  TX bytes:21761 (21.7 KB)
          Memory:e4600000-e4620000 

root@abacus:~# ping -b 172.20.0.255
WARNING: pinging broadcast address
PING 172.20.0.255 (172.20.0.255) 56(84) bytes of data.
^C
--- 172.20.0.255 ping statistics ---
9 packets transmitted, 0 received, 100% packet loss, time 8060ms

root@abacus:~# traceroute google.com
google.com: Name or service not known
Cannot handle "host" cmdline arg `google.com' on position 1 (argc 1)


```

---

### Post by shoaibi on 2008-11-22
also
on client:
```

route add -net 10.0.0.138 netmask 0.0.0.0 dev eth0
SIOCADDRT: Invalid argument

```

---

