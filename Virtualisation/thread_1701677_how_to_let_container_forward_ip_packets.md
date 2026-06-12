---
title: "how to let container forward ip packets"
date: 2011-03-06
forum: Virtualisation
---

### Post by volvolinux on 2011-03-06
Hello

I've setup two interfaces in my container, eth0 and eth1.

the ip address of eth0 is 192.168.1.8/24
the ip address of eth1 is 172.16.0.3/24

when i ping 172.16.0.3 from my web server 192.168.1.4, I found the ping is failed.

Then I turned on the tcpdump on interface eth1 and I saw that:

06:17:27.373507 IP 192.168.1.4 > 172.16.0.3: ICMP echo request, id 11023, seq 1134, length 64
06:17:28.373521 IP 192.168.1.4 > 172.16.0.3: ICMP echo request, id 11023, seq 1135, length 64
06:17:29.373524 IP 192.168.1.4 > 172.16.0.3: ICMP echo request, id 11023, seq 1136, length 64
06:17:30.373530 IP 192.168.1.4 > 172.16.0.3: ICMP echo request, id 11023, seq 1137, length 64

there is only echo in but no echo reply.

So, I think the problem is that the icmp packet reached my container buy it doesn't know how to forward it.

the route table in my container is:
root@r02:/# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
172.16.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 192.168.1.2 0.0.0.0 UG 100 0 0 eth0
0.0.0.0 172.16.0.1 0.0.0.0 UG 100 0 0 eth1

When I try to use sysctl -p command to see my sysctl configuraton, it says:

root@r02:/# sysctl -p
error: permission denied on key 'kernel.printk'
error: permission denied on key 'kernel.maps_protect'
error: permission denied on key 'fs.inotify.max_user_watches'
error: "vm.mmap_min_addr" is an unknown key
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.default.proxy_arp = 1
net.ipv4.ip_forward = 1
net.ipv4.conf.all.rp_filter = 1
error: permission denied on key 'kernel.sysrq'
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.all.send_redirects = 0

Is there something need to be done on sysctl regarding on VZ?

Thanks you in advance.

---

### Post by volvolinux on 2011-03-07
Hi, I am sorry that I forgot to say what virtulization I used.
 
I use openvz in Ubuntu 8.04

---

### Post by stlsaint on 2011-03-07
Im thinking bridge! [http://wiki.openvz.org/Using_private_IPs_for_Hardware_Nodes](http://wiki.openvz.org/Using_private_IPs_for_Hardware_Nodes)

hopefully that can get you going

---

### Post by volvolinux on 2011-03-12
Hello, I tried to look into it.
 
I think the problem is on Hardware node, however, I am not very familir with linux routing trouble shooting.
 
let's say that my machine A has the ip address of 192.168.1.4 and the gateway is 192.168.1.8, from this machine I try to ping the Hardware node, which is 172.16.0.2
 
[IMG]http://hiphotos.baidu.com/fpkk47/pic/item/0fde5c84b2d9f746b21bba8e.jpg[/IMG]
 
on the hardware node.
 
i see that:
 
root@yycat:/proc/sys/net/bridge# tcpdump -i br1 -nn icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on br1, link-type EN10MB (Ethernet), capture size 96 bytes
17:03:06.243535 IP 192.168.1.4 > 172.16.0.2: ICMP echo request, id 4932, seq 14, length 64
17:03:06.243874 IP 192.168.1.4 > 172.16.0.2: ICMP echo request, id 4932, seq 14, length 64
17:03:07.243382 IP 192.168.1.4 > 172.16.0.2: ICMP echo request, id 4932, seq 15, length 64
17:03:07.243564 IP 192.168.1.4 > 172.16.0.2: ICMP echo request, id 4932, seq 15, length 64
4 packets captured
4 packets received by filter
0 packets dropped by kernel
 
 
 
 
 
there is no echo reply, but the packge is reached on 172.16.0.2 machine, why no echo reply?
 
I check all the iptables and _[COLOR=#0000ff]/proc/sys/net/bridge [/COLOR]_are all set to 0
 
my kernel routing table is:
 
root@yycat:/proc/sys/net/bridge# route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 br0
172.16.0.0 0.0.0.0 255.255.255.0 U 0 0 0 br1
0.0.0.0 192.168.1.2 0.0.0.0 UG 100 0 0 br0
0.0.0.0 172.16.0.1 0.0.0.0 UG 100 0 0 br1
 
 
can some one give me some tips?

---

