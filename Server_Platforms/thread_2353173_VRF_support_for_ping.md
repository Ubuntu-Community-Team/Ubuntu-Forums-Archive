---
title: "VRF support for ping"
date: 2017-02-19
forum: Server Platforms
---

### Post by bizzy07 on 2017-02-19
I'm working on configuring multiple VRFs on Ubuntu Server 16.10 and having trouble using ping to validate the configuration. I've been using [https://www.kernel.org/doc/Documentation/networking/vrf.txt](https://www.kernel.org/doc/Documentation/networking/vrf.txt) for reference.
My configuration is:
Server: eth0.20 - 192.168.20.50/24 - GW 192.168.20.1
Router: port1(VLAN20) - 192.168.20.1/24
From the router, I can ping the server address at 192.168.20.50. The arp entry on the router for the server is correct and tcpdump on the server confirms pings are hitting eth0.20.
However, the server can't ping 192.168.20.1. It does have an ARP entry for the router interface which makes me think this is an issue with how I'm using being. Below is the ping and resulting output. 

    ```
 ping -I red 192.168.20.1
     ping: Warning: source address might be selected on device other than red
     ping: sendmsg: Network is unreachable
```


     ```
ping -I eth0.20 192.168.20.1
     ping 192.168.20.1 (192.168.20.1) from 192.168.20.50 eth0.20: 56(86) bytes of data.
     ping: sendmsg: Network is unreachable

```
Any assistance is much appreciated!

---

### Post by wildmanne39 on 2017-02-19
*Thread moved to **Server Platforms**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by The Cog on 2017-02-19
Can you please post the output of the commands **ifconfig**. Also, soon after attempting the ping, the command **ip neighbor**.
And even better, can you run **tcpdump -npe** for maybe 5 seconds while you are trying to ping, and post its output.

---

### Post by bizzy07 on 2017-02-19
```

root@server:/home/k# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::a00:27ff:febb:ad61  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:bb:ad:61  txqueuelen 1000  (Ethernet)
        RX packets 40  bytes 10974 (10.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 245  bytes 17606 (17.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.118  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::a00:27ff:feba:559d  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:ba:55:9d  txqueuelen 1000  (Ethernet)
        RX packets 766  bytes 65445 (65.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 467  bytes 54016 (54.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eth0.20: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.20.50  netmask 255.255.255.0  broadcast 192.168.20.255
        inet6 fe80::a00:27ff:febb:ad61  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:bb:ad:61  txqueuelen 1000  (Ethernet)
        RX packets 5  bytes 344 (344.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 37  bytes 3006 (3.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


eth0.30: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.30.50  netmask 255.255.255.0  broadcast 192.168.30.255
        inet6 fe80::a00:27ff:febb:ad61  prefixlen 64  scopeid 0x20<link>
        ether 08:00:27:bb:ad:61  txqueuelen 1000  (Ethernet)
        RX packets 5  bytes 230 (230.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 195  bytes 11906 (11.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 382  bytes 29342 (29.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 382  bytes 29342 (29.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


red: flags=1217<UP,RUNNING,NOARP,MASTER>  mtu 65536
        ether 5a:ee:10:b7:fb:49  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 6 overruns 0  carrier 0  collisions 0

```

ip neighbor. 

```

root@server:/home/k# ping 192.168.20.1 -I red
ping: Warning: source address might be selected on device other than red.
PING 192.168.20.1 (192.168.20.1) from 192.168.20.50 red: 56(84) bytes of data.
^C
--- 192.168.20.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6152ms


root@server:/home/k# ping 192.168.20.1 -I eth0.20
PING 192.168.20.1 (192.168.20.1) from 192.168.20.50 eth0.20: 56(84) bytes of data.
^C
--- 192.168.20.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2042ms


root@server:/home/k# ip neighbor
192.168.30.1 dev eth0.30 lladdr 90:6c:ac:5b:a1:55 REACHABLE
192.168.1.115 dev eth1 lladdr a4:4e:31:28:77:cc REACHABLE
192.168.1.99 dev eth1 lladdr 90:6c:ac:5b:a1:53 STALE

root@server:/home/k# ip neigh show dev red
root@server:/home/k# 



```

tcpdump

```

root@server:/home/k# tcpdump -npe -i eth0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
19:34:32.453191 08:00:27:bb:ad:61 > 90:6c:ac:5b:a1:55, ethertype 802.1Q (0x8100), length 102: vlan 30, p 0, ethertype IPv4, 192.168.30.50 > 192.168.20.1: ICMP echo request, id 1871, seq 1, length 64
19:34:33.088031 08:00:27:bb:ad:61 > 90:6c:ac:5b:a1:55, ethertype 802.1Q (0x8100), length 78: vlan 30, p 0, ethertype IPv4, 192.168.30.50.51483 > 66.60.130.158.53: 10265+ A? ntp.ubuntu.com. (32)
19:34:33.486264 08:00:27:bb:ad:61 > 90:6c:ac:5b:a1:55, ethertype 802.1Q (0x8100), length 102: vlan 30, p 0, ethertype IPv4, 192.168.30.50 > 192.168.20.1: ICMP echo request, id 1871, seq 2, length 64
19:34:34.510629 08:00:27:bb:ad:61 > 90:6c:ac:5b:a1:55, ethertype 802.1Q (0x8100), length 102: vlan 30, p 0, ethertype IPv4, 192.168.30.50 > 192.168.20.1: ICMP echo request, id 1871, seq 3, length 64
^C
4 packets captured
4 packets received by filter


```


It looks like the server is sourcing the ping from another VLAN interface IP (VLAN30/192.168.30.50) that isn't part of the vrf. Also, looking at the source MAC, it's also assigned to VLAN30. Am I looking at that right?

---

### Post by The Cog on 2017-02-20
Yes it looks like it's using eth0.30's source address. 

But either of these should work:
```
ping 192.168.20.1
ping -I eth0.20 192.168.20.1
```
As 192.168.20.0/24 is locally connected to eth0.20, that's the interface it should choose to use without having to be told. 

Here's a trace of my test using VLAN 10 and the command **ping 10.0.0.104**:

```
09:28:46.631763 bc:5f:f4:2a:cf:24 > ff:ff:ff:ff:ff:ff, ethertype 802.1Q (0x8100), length 46: vlan 10, p 0, ethertype ARP, Request who-has 10.0.0.104 tell 10.0.0.101, length 28
09:28:46.631962 00:24:54:11:a2:0f > bc:5f:f4:2a:cf:24, ethertype 802.1Q (0x8100), length 64: vlan 10, p 0, ethertype ARP, Reply 10.0.0.104 is-at 00:24:54:11:a2:0f, length 46
09:28:46.631983 bc:5f:f4:2a:cf:24 > 00:24:54:11:a2:0f, ethertype 802.1Q (0x8100), length 102: vlan 10, p 0, ethertype IPv4, 10.0.0.101 > 10.0.0.104: ICMP echo request, id 4071, seq 1, length 64
09:28:46.632137 00:24:54:11:a2:0f > bc:5f:f4:2a:cf:24, ethertype 802.1Q (0x8100), length 102: vlan 10, p 0, ethertype IPv4, 10.0.0.104 > 10.0.0.101: ICMP echo reply, id 4071, seq 1, length 64

```

All that works without the "master" interface.
Then I followed the instructions for the master interface that you linked, and got network unreachable when I tried to ping the router with -I vrf-blue, just like as you do.
I found I had to add the following line, to get the local network into the routing table (src is my eth0.10 address):
```
sudo ip ro add table 10 10.0.0.0/24 dev eth0.10  proto kernel  scope link  src 10.0.0.101
```
Then the ping to the router worked.

---

### Post by bizzy07 on 2017-02-20
I check and the local network route you added already existed for me. Seems to automatically move the route when I add the interface to the vrf. Would you mind sharing the kernel version and exact commands you're using? 

```


root@server:/home/k# ip link add blue type vrf table 20
root@server:/home/k# ip route add table 20 unreachable default
root@server:/home/k# ip link set dev eth0.20 master blue



```

```


root@server:/home/k# ip route list table 20
unreachable default 
broadcast 192.168.20.0 dev eth0.20  proto kernel  scope link  src 192.168.20.50 
192.168.20.0/24 dev eth0.20  proto kernel  scope link  src 192.168.20.50 
local 192.168.20.50 dev eth0.20  proto kernel  scope host  src 192.168.20.50 
broadcast 192.168.20.255 dev eth0.20  proto kernel  scope link  src 192.168.20.50 

root@server:/home/k# ip link show master blue
5: eth0.20@eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master blue state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:bb:ad:61 brd ff:ff:ff:ff:ff:ff

root@server:/home/k# ping 192.168.20.1 -I eth0.20
connect: Network is unreachable

root@server:/home/k# uname -a
Linux server 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux






```

---

### Post by The Cog on 2017-02-20
I originally started with these commands, which have nothing to do with VRF configuration:
```
iface=eth0
vlan=10
vconfig add eth0 10
ip addr add 10.0.0.101/24 dev eth0.10
ip link set up eth0.10
```

This seems to be enough to be able to ping 10.0.0.x without specifying extra arguments like -i or -I.

It seems the normal thing to do (without using the vrf interface configuration commands) is to continue with these commands (though I didn't earlier). 
The route add command is not quite the same as the one I posted earlier, it's probably better though either seemed to do the trick:
```
ip route add 10.0.0.0/24 table 10 dev eth0.10 proto static
ip rule add iif eth0.10 table 10
ip rule add oif eth0.10 table 10

```

Between them, the above should arrange that any process bound to the address of eth0.10 should use routing table 10 and encapsulate with vlan tag 10. There is no use of the vrf commands. This page helped me a lot: [http://www.adminarticles.com/vrf-lite-with-iproute2/](http://www.adminarticles.com/vrf-lite-with-iproute2/) . I would point out that the above is using a single interface as a trunk, carrying multiple vlans, all tagged with 802.1q VLAN numbers.


I messed around with the vrf commands you posted, and came to the conclusion that the problem was that the routing table didn't have the locally attached subnet listed in it which is why there was "network unreachable". Adding the route seemed to fix that. However, I also found that using those vrf commands broke the native eth0 connectivity. I think that perhaps the vrf configuration doesn't do vlan tagging at all, but instead enslaves a group of physical interfaces and captures them into a routing table in the same way that happens with a cisco router. 

I presume that you want to use multiple vlans on one physical interface as you have configured eth0.20 and eth0.30. 
Perhaps it is possible to combine vrf configuration with vlan tagging by enslaving tagged interfaces (e.g. eth0.20) into the vrfs rather that the base eth0 interface. I might get time to try that out tomorrow, but can't at the moment.

---

### Post by bizzy07 on 2017-02-21
Thanks for your help looking into this.

I've been trying by adding the VLAN interface eth0.20 to the VRF but haven't had any luck but obviously I'm missing something. Also, I was looking at [https://docs.cumulusnetworks.com/display/DOCS/Virtual+Routing+and+Forwarding+-+VRF](https://docs.cumulusnetworks.com/display/DOCS/Virtual+Routing+and+Forwarding+-+VRF) and their presentation seems to suggest that VRFs are fully compatible with VLANs (layer2 vs layer3 isolation) which makes sense but obviously I'm missing something. 

You're right about my overall goal. I'm trying to have each VLAN route through the default router even the traffic on VLAN20 is destined to an interface on VLAN30. I've played around with network namespaces but it seems like VRFs are the more light weight approach.

---

