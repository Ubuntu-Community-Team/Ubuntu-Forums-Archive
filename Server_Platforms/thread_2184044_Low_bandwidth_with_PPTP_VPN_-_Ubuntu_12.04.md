---
title: "Low bandwidth with PPTP VPN - Ubuntu 12.04"
date: 2013-10-27
forum: Server Platforms
---

### Post by Dominic--- on 2013-10-27
Hi,

I have setup a PPTP VPN between a Fedora OS and a Ubuntu Server (12.04).

Without a VPN both connections have a minimum of 2 Megabyte P/S download and a normal and fast connection.
The upload of both connections are at minimum 1Megabyte.

However, when I establish the PPTP VPN my bandwidth is dropping to 150/200 Kilobyte P/S download on client side .

When I ping I from the client to server within the VPN tunnel it shows a fluctuating response time (average around 150ms):

   root@Berlijn-SRV3:~# ping 10.99.99.100 
 PING 10.99.99.100 (10.99.99.100) 56(84) bytes of data. 

 64 bytes from 10.99.99.100: icmp_req=1 ttl=64 time=25.9 ms 
 64 bytes from 10.99.99.100: icmp_req=2 ttl=64 time=37.2 ms 
 64 bytes from 10.99.99.100: icmp_req=3 ttl=64 time=137 ms 
 64 bytes from 10.99.99.100: icmp_req=4 ttl=64 time=119 ms 
 64 bytes from 10.99.99.100: icmp_req=5 ttl=64 time=134 ms 
 64 bytes from 10.99.99.100: icmp_req=6 ttl=64 time=51.4 ms 
 64 bytes from 10.99.99.100: icmp_req=7 ttl=64 time=73.2 ms 
 64 bytes from 10.99.99.100: icmp_req=8 ttl=64 time=106 ms 
 64 bytes from 10.99.99.100: icmp_req=9 ttl=64 time=118 ms 
 64 bytes from 10.99.99.100: icmp_req=10 ttl=64 time=42.4 ms 
 64 bytes from 10.99.99.100: icmp_req=11 ttl=64 time=62.3 ms 
 64 bytes from 10.99.99.100: icmp_req=12 ttl=64 time=83.3 ms 
 64 bytes from 10.99.99.100: icmp_req=13 ttl=64 time=107 ms 
 64 bytes from 10.99.99.100: icmp_req=14 ttl=64 time=148 ms 
 64 bytes from 10.99.99.100: icmp_req=15 ttl=64 time=51.5 ms 
 64 bytes from 10.99.99.100: icmp_req=16 ttl=64 time=75.3 ms 
 64 bytes from 10.99.99.100: icmp_req=17 ttl=64 time=96.3 ms 
 64 bytes from 10.99.99.100: icmp_req=18 ttl=64 time=120 ms 
 64 bytes from 10.99.99.100: icmp_req=19 ttl=64 time=36.4 ms 
 64 bytes from 10.99.99.100: icmp_req=20 ttl=64 time=64.3 ms 
 64 bytes from 10.99.99.100: icmp_req=21 ttl=64 time=85.3 ms 
 64 bytes from 10.99.99.100: icmp_req=22 ttl=64 time=105 ms 
 64 bytes from 10.99.99.100: icmp_req=23 ttl=64 time=129 ms 
 64 bytes from 10.99.99.100: icmp_req=24 ttl=64 time=50.4 ms 
 64 bytes from 10.99.99.100: icmp_req=25 ttl=64 time=73.3 ms 
 64 bytes from 10.99.99.100: icmp_req=26 ttl=64 time=96.3 ms 
 64 bytes from 10.99.99.100: icmp_req=27 ttl=64 time=119 ms 
 64 bytes from 10.99.99.100: icmp_req=28 ttl=64 time=36.4 ms 
 64 bytes from 10.99.99.100: icmp_req=29 ttl=64 time=60.3 ms 
 64 bytes from 10.99.99.100: icmp_req=30 ttl=64 time=82.3 ms 
 64 bytes from 10.99.99.100: icmp_req=31 ttl=64 time=105 ms 
 64 bytes from 10.99.99.100: icmp_req=32 ttl=64 time=138 ms 
 64 bytes from 10.99.99.100: icmp_req=33 ttl=64 time=46.4 ms 
 64 bytes from 10.99.99.100: icmp_req=34 ttl=64 time=77.3 ms 
 64 bytes from 10.99.99.100: icmp_req=35 ttl=64 time=94.3 ms 
 ^C 
 --- 10.99.99.100 ping statistics --- 
 35 packets transmitted, 35 received, 0% packet loss, time 34048ms 
 rtt min/avg/max/mdev = 25.913/85.505/148.382/33.835 ms 

When I do the same without the VPN tunnel it shows an average delay of 31ms.
   
      PING xxxx.xxxxx.nl (x.x.x.x) 56(84) bytes of data. 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=1 ttl=52 time=24.8 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=2 ttl=52 time=37.7 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=3 ttl=52 time=33.1 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=4 ttl=52 time=30.4 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=5 ttl=52 time=29.9 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=6 ttl=52 time=29.1 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=8 ttl=52 time=30.3 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=9 ttl=52 time=29.6 ms 
 64 bytes from domain.fqdn.com (x.x.x.x): icmp_seq=10 ttl=52 t

---

### Post by houstonbofh on 2013-10-29
Do a traceroute while outside the VPN...  See who is in the middle.  My first guess would be DPI throttling VPN traffic.  I mean, the only people that use it are those dirty pirates... (/sarcasm)

---

### Post by Dominic--- on 2013-10-30
Haha.

I tracerouted the connection from point A to B outside the VPN but didn't noticed anything strange. Besides, even when I don't encrypt the data transferred over the VPN tunnel the bandwidth doesn't change. 

But, in the meantime I found a workaround, not a solution though. My setup was as follows: My OS on the client was running Fedora, my VPN server was Ubuntu 12.04 LTS. With the host itself and VM's within the host (Linux and Windows) the VPN connection was slow. However, when I ran Wireshark I notices that my host and VM's were transmitting al kinds of TCP Retransmissions, so the host and vhosts were sending traffic, but the host didn't see traffic returning. With a Windows laptop on the same subnet there were no problems and I was able to get the full speed within the VPN tunnel. When I changes my OS on the client from Linux to Windows the problem was solved...  When running a virtual Linux machine on a Windows host I also don't run into problems. I think that my Fedora had some issues with my NIC driver (Linksys USB).

---

