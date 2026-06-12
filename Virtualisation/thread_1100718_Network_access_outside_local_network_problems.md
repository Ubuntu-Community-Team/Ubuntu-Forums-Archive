---
title: "Network: access outside local network problems"
date: 2009-03-19
forum: Virtualisation
---

### Post by GoBieN on 2009-03-19
Hey,

I'm running the latest Ubuntu server version (intrepid), and have since 2 weeks a strange problem.

I cannot reach the server anymore from the internet (i have port mappings in place). I also can't do a traceroute or ping on the shell to the internet:
```
root@hercules:~# uname -a
Linux hercules.domain.tld 2.6.24-21-xen #1 SMP Wed Oct 22 02:11:27 UTC 2008 i686 GNU/Linux
root@hercules:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 9e:61:38:c7:07:e6
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9c61:38ff:fec7:7e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1107993 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:451206372 (451.2 MB)  TX bytes:197973608 (197.9 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:457520 (457.5 KB)  TX bytes:457520 (457.5 KB)

root@hercules:~# ping 195.130.130.5
PING 195.130.130.5 (195.130.130.5) 56(84) bytes of data.
From 192.168.1.3 icmp_seq=1 Destination Port Unreachable
From 192.168.1.3 icmp_seq=2 Destination Port Unreachable
From 192.168.1.3 icmp_seq=3 Destination Port Unreachable
From 192.168.1.3 icmp_seq=4 Destination Port Unreachable

--- 195.130.130.5 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 2999ms

root@hercules:~# traceroute 195.130.130.5
traceroute to 195.130.130.5 (195.130.130.5), 30 hops max, 40 byte packets
 1  hercules (192.168.1.3)  0.359 ms  0.383 ms  0.390 ms
root@hercules:~#
```

So ping doesn't work, and traceroute ends at himself ?
Below my hosts file and output of route and network config:
```
root@hercules:~# cat /etc/hosts
127.0.0.1       hercules.domain.tld localhost hercules
192.168.1.3     hercules.domain.tld hercules
192.168.1.2     w2003r2 w2003r2.domain.tld
192.168.1.250   Firewall

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
root@hercules:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         Firewall        0.0.0.0         UG    0      0        0 eth0
root@hercules:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.250
root@hercules:~#
```

Strange thing is, updates with aptitude work fine, also lynx the CLI browser can access the Internet.

On my Firewall (it's the default gateway) i have rules in place that allow traffic from ANY to ANY, and all other PC's in the network can do ping/traceroute just fine.


Firewall logs:
```
2009-03-19 19:56:43	174.36.1.123:59610	84.192.1.27:8080	174.36.1.123:59610	192.168.1.3:8080	TCP PORT 8080	20 sec.	234	0	Close - AGE OUT
```
Please advise !

---

### Post by GoBieN on 2009-03-21
bump ?

---

### Post by GoBieN on 2009-03-30
anyone please ?

---

### Post by Iowan on 2009-03-30
Do pings work internally - Hercules can ping Firewall/other machines and other internal machines can ping Hercules?

---

### Post by GoBieN on 2009-03-30
> **Iowan said:**
> Do pings work internally - Hercules can ping Firewall/other machines and other internal machines can ping Hercules?

thanks for the reply.
Internally all works excellent, Hercules can ping Firewall and other hosts.

ps: Hercules is a VM on Xenserver, but i have another VM (windows) that works fine.

---

### Post by bodhi.zazen on 2009-03-31
Moved to virtualization :)

---

