---
title: "ip ping is continuous, dns ping is disconinuous"
date: 2010-08-05
forum: Server Platforms
---

### Post by fdelval on 2010-08-05
Hello all

When i ping [www.google.es]("http://www.google.es"), i get something like:

> ping [www.google.es]("http://www.google.es")
(wait 20 seconds)
64 bytes from 66.249.92.104: icmp_seq=2 ttl:53 time=80 ms
(wait 10 seconds)
64 bytes from 66.249.92.104: icmp_seq=3 ttl:53 time=84 ms
(wait 10 seconds)
64 bytes from 66.249.92.104: icmp_seq=4 ttl:53 time=81 msMeanwhile if i ping one of google's ip, i get

> ping 66.249.92.104
64 bytes from 66.249.92.104: icmp_seq=2 ttl:53 time=80 ms
64 bytes from 66.249.92.104: icmp_seq=3 ttl:53 time=84 ms
64 bytes from 66.249.92.104: icmp_seq=4 ttl:53 time=81 msThe time is the same, ~80ms, but the time elapsed from output to output in command line is 10 seconds or less...


INTERFACES:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.3.251
        netmask 255.255.255.0

auto eth1
iface eth1 inet static
        address 192.168.4.251
        netmask 255.255.255.0

auto eth2
iface eth2 inet static
        address 192.168.10.251
        netmask 255.255.255.0
Route table:

> 
192.168.4.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.4.4     0.0.0.0         UG    0      0        0 eth1
/etc/resolv.conf
[B]ORIGINALLY, THE SETUP WAS MISSING THE /ETC/RESOLV.CONF FILE; SO I CREATED IT AND FILLED UP WITH THIS:

[/B]> nameserver 80.58.61.254The server is a router, and its weird, because if i ping from one of the lan's compuiters connected to the router, the pings are fast in both ways...


tips¿¿

*ubuntu 9.10 32 bits server, with aptitude update done.
*server ip is 192.168.4251, and router is 192.168.4.4

---

### Post by stlsaint on 2010-08-05
SO......exactly what is it that you are needing help on?

---

### Post by fdelval on 2010-08-11
oops, sorry for the delay

well, dont you find nothing suspicious there? something could cause trouble i think

help could be either: 
nothing is wrong its normal, or, check this use this command and fix it

---

