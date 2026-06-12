---
title: "WAN IP Pinging but LAN IP's are not Pinging"
date: 2018-01-28
forum: Server Platforms
---

### Post by slkamath on 2018-01-28
Hi,

Myself Lokesh Kamath.

I am using Ubuntu 16.04LTS Server.

Recently there was issue with our old server and we have newly installed Ubuntu Server 16.04LTS.

This Machine is work as router.

In the Server 3 LAN Cards and it's em1, em2, em3

em1 - ISP WAN IP (Static)
IP 203.92.XX.XXX
Mask 255.255.255.252
GW 203.92.XX.XXX

#em2 - LAN Pool IP from ISP (Static) (assigned IP but not activated)
#IP 180.151.XX.XX
#Mask 255.255.255.248

em3 - Local LAN
IP 192.192.0.1
Mask 255.255.255.0
GW 192.192.0.1 (tried with GW & without GW)

Now I am getting internet through em1 (ALL WAN IP I can ping). 

Ping Output:
root@lesvr3:/home/administrator# ping google.com
PING google.com (216.58.203.206) 56(84) bytes of data.
64 bytes from bom07s12-in-f14.1e100.net (216.58.203.206): icmp_seq=1 ttl=55 time=24.2 ms
64 bytes from bom07s12-in-f14.1e100.net (216.58.203.206): icmp_seq=2 ttl=55 time=23.5 ms
64 bytes from bom07s12-in-f14.1e100.net (216.58.203.206): icmp_seq=3 ttl=55 time=22.9 ms
64 bytes from bom07s12-in-f14.1e100.net (216.58.203.206): icmp_seq=4 ttl=55 time=23.2 ms
64 bytes from bom07s12-in-f14.1e100.net (216.58.203.206): icmp_seq=5 ttl=55 time=23.1 ms
^C
--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 22.992/23.449/24.279/0.484 ms
============================================
root@lesvr3:/home/administrator# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=47 time=44.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=47 time=43.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=47 time=43.7 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=47 time=43.6 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=47 time=43.8 ms
^C
--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 43.570/43.818/44.254/0.271 ms
============================================

I can also ping 192.192.0.1(self ping).

Ping Output:
root@lesvr3:/home/administrator# ping 192.192.0.1
PING 192.192.0.1 (192.192.0.1) 56(84) bytes of data.
64 bytes from 192.192.0.1: icmp_seq=1 ttl=64 time=0.012 ms
64 bytes from 192.192.0.1: icmp_seq=2 ttl=64 time=0.013 ms
64 bytes from 192.192.0.1: icmp_seq=3 ttl=64 time=0.009 ms
64 bytes from 192.192.0.1: icmp_seq=4 ttl=64 time=0.011 ms
64 bytes from 192.192.0.1: icmp_seq=5 ttl=64 time=0.020 ms
^C
--- 192.192.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3996ms
rtt min/avg/max/mdev = 0.009/0.013/0.020/0.003 ms
=================================================

 but other network address I cant ping also I cant ping from Local LAN to 192.192.0.1.

Ping Output:
root@lesvr3:/home/administrator# ping 192.192.0.100
PING 192.192.0.100 (192.192.0.100) 56(84) bytes of data.
From 192.192.0.1 icmp_seq=1 Destination Host Unreachable
From 192.192.0.1 icmp_seq=2 Destination Host Unreachable
From 192.192.0.1 icmp_seq=3 Destination Host Unreachable


Please guide me to solve this issue.

Thanks in advance.

Lokesh Kamath

---

### Post by TheFu on 2018-01-28
You can't just pick any internal IPs you want randomly, if you want things to work easily.
192.192.0.1 - is a public IP address.  I suspect you want 192.168.x.x/24 as the LAN subnet.

Since it is a router, showing the routing table is necessary.  **route -n**
Please use code tags when posting output. Editing the first post that way out be helpful.

---

### Post by slkamath on 2018-01-28
> **TheFu said:**
> You can't just pick any internal IPs you want randomly, if you want things to work easily.
192.192.0.1 - is a public IP address.  I suspect you want 192.168.x.x/24 as the LAN subnet.

Since it is a router, showing the routing table is necessary.  **route -n**
Please use code tags when posting output. Editing the first post that way out be helpful.

Thanks for your info.

But We are using this from last 15 years. (I can understand 192.192.0.1 series is public ip) we are using that ip address as local lan ip.

Output of - route -n

root@lesvr3:/home/administrator# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         203.92.62.153   0.0.0.0         UG    0      0        0 em1
192.192.0.0     0.0.0.0         255.255.255.0   U     0      0        0 em3
203.92.62.152   0.0.0.0         255.255.255.252 U     0      0        0 em1 

Lokesh Kamath

---

### Post by volkswagner on 2018-01-28
I agree with TheFu. You may not get much help
with such a misconfiguration.

One thing though, make sure you have allowed
the [server to forward packets]("http://www.microhowto.info/howto/enable_forwarding_of_ipv4_packets.html").

Edit /etc/sysctl.conf and enable/uncomment net.ipv4.ip_forward=1

---

### Post by slkamath on 2018-01-29
> **TheFu said:**
> You can't just pick any internal IPs you want randomly, if you want things to work easily.
192.192.0.1 - is a public IP address.  I suspect you want 192.168.x.x/24 as the LAN subnet.

Since it is a router, showing the routing table is necessary.  **route -n**
Please use code tags when posting output. Editing the first post that way out be helpful.

If I change the LAN IP to 192.168.X.X/24 then what changes I have to do in my network to get ping and to use internet?

Lokesh Kamath

---

### Post by slkamath on 2018-01-29
Thanks for your response.

That changes I have already done.

---

### Post by slkamath on 2018-01-29
> **volkswagner said:**
> I agree with TheFu. You may not get much help
with such a misconfiguration.

One thing though, make sure you have allowed
the [server to forward packets]("http://www.microhowto.info/howto/enable_forwarding_of_ipv4_packets.html").

Edit /etc/sysctl.conf and enable/uncomment net.ipv4.ip_forward=1

Thanks for your response.

That changes I have already done.

---

### Post by slkamath on 2018-01-30
Thanks to one & all. YUREKA :)

You can close this thread. Did few changes and It started working for me. :)



Lokesh Kamath

---

