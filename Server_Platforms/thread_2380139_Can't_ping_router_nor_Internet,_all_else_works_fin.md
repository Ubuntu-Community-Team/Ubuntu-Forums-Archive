---
title: "Can't ping router nor Internet, all else works fine"
date: 2017-12-13
forum: Server Platforms
---

### Post by frontrow3 on 2017-12-13
This is a tough one and I have been working on it for a long, long time.  I have found a few other threads that describe similar problems but no solutions.  They either die with no solution or end with "I don't know why but I restarted my server and now it is working fine all of a sudden".  That didn't work for me.

I have Ubuntu server 14.04 running Bind9, dhcpd, apache, a couple other services.  It has a static IP of 192.168.1.11.  It connects to a Netgear GS724T smart switch (192.168.1.2) and that connects to a Netgear C6300 router (192.168.1.1) which is the default gateway to the Inet.  Smart switch also connects to a local network with a few PCs on DHCP, a Windows server with a static IP, a CentOS server with a static IP, a couple of printers with static IPs,  phone adapter with static IP, and a network disks with static IP.

Bind is working for the local network (limited to local).  It serves a bunch of domain names for testing websites on the Apache, among other things.
DHCP server is working for the local network assigning addresses 192.168.1.101 thru 150
Apache serves sites to the local network just fine
Local PCs and servers can ping 192.168.1.11 and it can ping them too.
Local PCs and other servers can ping each other, the switch, and the router and the router can ping them back
Local PCs and other servers can access the Internet just fine.

Problem: My 192.168.1.11 server cannot ping the router nor can the router cannot ping it and the 11 server has no Internet access too (neither incoming nor outgoing).

Odd: Traceroute from the 11 server to all local network and Inet addresses fails UNLESS I use "traceroute -I", in which case it traces just fine with 1 hop to local network addresses (but fails to Inet address or IPs on the 2nd hop with a "!H" (Host not reachable from gateway.)).  Output from those is below:

```
user@11server:/$ sudo traceroute localpc1                                                         #traceroute fails
traceroute to localpc1 (192.168.1.105), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


user@11server:/$ sudo traceroute -I localpc1                                                   #traceroute -I works!
traceroute to localpc1 (192.168.1.105), 30 hops max, 60 byte packets
 1  localpc1.xxx.lan (192.168.1.105)  0.439 ms  0.432 ms  0.490 ms


user@11server:/$ sudo traceroute -I 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  11server.xxx.lan (192.168.1.11)  2996.400 ms !H * *                                   #Finds the DNS server on the first hop but fails to get to the forwarder: Internet not accessible


user@11server:/$ sudo traceroute -I google.com
google.com: Name or service not known                                                         #Cannot get to forwarder DNS server on Internet to resolve google.com
Cannot handle "host" cmdline arg `google.com' on position 1 (argc 2)

```

The problem seems to be limited to the communication between my 11 server and my router AND to UDP and not TCP traffic, right?

I have tried many things, among them:
1. Restart both 11 server and router and switch a few times each.  ODD: when I restart the router IT WORKS FINE for a short time, maybe less than 1 minute, but then reverts to above.  Huh?!?
2. Disable the firewall on 11 server: no affect
3. Disabled IPv6 on 11 server (and it remains disabled).  I did this because of some comments that I found in other threads.

I will post whatever config files are asked for tomorrow but because the local network, Bind9, dhcpd, Apache, local ping, traceroute -I and a few other things work fine AND because of testing that I have done I THINK that I have ruled out:
1. Router on different subnet, it is not
2. Cabling and port problems
3. Firewall interference....unless there is a 2nd firewall besides ucf that I don't know about.
4. selinux because it is disabled on this server
5. IP address conflict....unless there is possibly some hidden device on the network that is using 192.168.1.11 too.  But it is NOT being assigned by the DHCP server and I have confirmed that my other 2 static IP servers are 192.168.1.12 and 192.168.1.13.  I have my IP addresses written down in a list and the network is not THAT large.

I am at a loss.  Anyone got any ideas?

Thanks.


sudo route -n
```
user@11server:/$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```


ip route list
```
user@11server:/$ ip route list
default via 192.168.1.1 dev eth0
169.254.0.0/16 dev eth0  scope link  metric 1000
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.11

```


ip link list
```
user@11server:/$ ip link listbob@pe1750-3:/$ ifconfigeth0      Link encap:Ethernet  HWaddr 00:0b:db:94:20:e3
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34625381 (34.6 MB)  TX bytes:8685401 (8.6 MB)
          Interrupt:16


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17195511 (17.1 MB)  TX bytes:17195511 (17.1 MB)


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN mode DEFAULT group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:0b:db:94:20:e3 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:0b:db:94:20:e4 brd ff:ff:ff:ff:ff:ff

```


From 13server:
```
[user@13server ~]$ ping 192.168.1.11
PING 192.168.1.11 (192.168.1.11) 56(84) bytes of data.
64 bytes from 192.168.1.11: icmp_seq=1 ttl=64 time=0.155 ms
64 bytes from 192.168.1.11: icmp_seq=2 ttl=64 time=0.106 ms
^C
--- 192.168.1.11 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1379ms
rtt min/avg/max/mdev = 0.106/0.130/0.155/0.027 ms


[user@13server ~]$ ip nei list
fe80::526a:3ff:fe7e:2f72 dev eth0 lladdr 50:6a:03:7e:2f:72 router REACHABLE
192.168.1.1 dev eth0 lladdr 50:6a:03:7e:2f:72 REACHABLE
192.168.1.11 dev eth0 lladdr 00:0b:db:94:20:e3 REACHABLE
192.168.1.103 dev eth0 lladdr 00:21:6a:26:d7:c6 REACHABLE

```

To compare:
```
user@11server:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:94:20:e3
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:277820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34625381 (34.6 MB)  TX bytes:8685401 (8.6 MB)
          Interrupt:16


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94935 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94935 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17195511 (17.1 MB)  TX bytes:17195511 (17.1 MB)

```

---

### Post by darkod on 2017-12-13
It looks like somehow it is trying to use itself for routing instead of using the router. When trying traceroute -I 8.8.8.8 I think the first hop should not be .1.11 (the server itself).

What does your routing table look like:
```
route -n
```

---

### Post by The Cog on 2017-12-13
I think I would like to see the output of **ip route list** and **ip link list**. 

I am thinking ip conflict. Can you go to one of the other devices and do **ping 192.168.1.11** and then **ip nei list** to get the MAC address they are talking to. Compare this against the lp link list from 11server. If the MAC address of .11 has changed then you definitely have duplicate .11 devices.

---

### Post by frontrow3 on 2017-12-14
@Darko, thanks for your help.  Output of "route -n" has been added to the post.  What is the 169.254.0.0 IP address?

---

### Post by frontrow3 on 2017-12-14
@The Cog, thanks for helping.  I have added output as requested above.  The IP addresses are the same.  Good thought to check that, though.

---

### Post by darkod on 2017-12-14
The route looks correct, 192.168.1.1 is default gateway. I am also little confused with what you added above, that it works for a short while after a router restart.

If you have a problem with the server a router restart shouldn't matter and change behavior. Which it does.

The check if it's really the router restart or just the network disconnect, can you try unplugging the ethernet cable and then plugging it again? That will simulate cable disconnect. Does it work for a short while after that?

If cable disconnect makes no difference but router restart does, I would start looking more into the router. But I have no idea how at this moment...

Also, your smart switch has IP of .1.2 but it has nothing to do with any routing, filtering, etc, right? Because switch is usually just that, used to connect the network together. However a smart switch with options can have something you are using that could produce a problem. But on the other hand it is strange only one server to be affected...

---

### Post by The Cog on 2017-12-14
169.254.0.0 is an autoconfigured IP address, intended to be used for local-net communication only if there is no proper network address. You can ignore it.

I don't see any evidence of a duplicate IP in your output, so I am somewhat bemused. I think at this stage I would resort to using tcpdump to watch packets and responses. First, let's try and ping the router. On 11server open two command prompts. In one run the command:
```
sudo tcpdump -npe -i eth0 icmp or arp
```
And while that's running, in the other window run:
```
ping 192.168.1.1
```
We probably only need the first ten lines from tcpdump - they are probably all repeats anyway.

It would be **very** interesting to do the same thing shortly after the router was rebooted so the ping works as well, so we can compare the behaviour on the network between working and not.

This may not tell us what's happening without further investigation, but it's a necessary first step in finding out.

---

### Post by frontrow3 on 2017-12-14
@ Darko, thanks for your analysis.

I had previously tried disconnecting the cable at 11server; no affect.  I just tried it again and same; no affect.

One thing that I just noticed on another ping attempt is that it says there are errors:

```
user@11server:/$ ping 192.168.1.1PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.11 icmp_seq=3 Destination Host Unreachable
From 192.168.1.11 icmp_seq=5 Destination Host Unreachable
From 192.168.1.11 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
7 packets transmitted, 0 received, **+3 errors**, 100% packet loss, time 6030ms
pipe 2

```

Does that shed any light?

The smart switch has nothing configured in it; I am really just using it a a dumb switch.  All ports have Flow Control enabled and QOS set to Normal.  All 24 ports are members of the single vlan and there is no trunking configured.

---

### Post by The Cog on 2017-12-14
Destination Host Unreachable is probably that you are not getting ARP responses. Try the command **ip ne list** or **arp -n** just after you get the host unreachable.

---

### Post by frontrow3 on 2017-12-14
@The Cog, thanks for your work.

Output from tcpdump requested is below:

```
user@11server:/etc/network$ sudo tcpdump -npe -i eth0 icmp or arptcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
12:02:35.679894 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.105 tell 192.168.1.11, length 28
12:02:35.680023 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Reply 192.168.1.105 is-at 00:12:3f:88:3d:0c, length 46
12:02:39.276229 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:40.275902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:41.275903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:42.276336 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:43.275902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:44.275898 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:45.276310 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:45.312145 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
12:02:45.312161 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:02:46.275903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:47.264926 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:02:47.275901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:48.276192 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:49.223066 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:02:49.275895 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:50.275902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:02:50.746610 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
^C
19 packets captured
19 packets received by filter
0 packets dropped by kernel

```
Seems like 11 asks but the router never answers, right?

As you can see, there is some other traffic in there too.  One thing that strikes me as odd is that there is the line that contains "Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46".  Is that normal?  Why would 13 need to be asking for its own number?  Does that indicate anything to you?

So I ran the tcpdump command again, this time WITHOUT ping running.  Results:

```
user@11server:/etc/network$ sudo tcpdump -npe -i eth0 icmp or arptcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
12:13:34.295902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:37.221517 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:38.219903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:39.219899 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:40.772539 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:41.771900 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:42.771895 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:43.231897 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.105 tell 192.168.1.11, length 28
12:13:43.232037 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Reply 192.168.1.105 is-at 00:12:3f:88:3d:0c, length 46
12:13:46.254517 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:47.251904 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:48.225015 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
12:13:48.225040 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:13:48.251902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:49.192589 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.105, length 46
12:13:49.192614 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:13:49.773172 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:50.620596 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
12:13:50.771902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:51.771900 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:53.174822 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:13:55.129899 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:13:55.254564 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:56.251905 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:57.251904 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:58.582535 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:13:58.949569 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:13:59.947903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:00.947904 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:01.129948 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:14:01.423809 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
12:14:11.421903 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
12:14:11.720302 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
12:14:11.720317 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:14:22.229196 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:23.227905 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:23.686440 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.105, length 46
12:14:23.686457 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:14:24.164051 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:14:24.227903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:25.903895 00:0b:db:94:20:e3 > 60:67:20:f7:9b:3c, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.114 tell 192.168.1.11, length 28
12:14:25.908261 60:67:20:f7:9b:3c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Reply 192.168.1.114 is-at 60:67:20:f7:9b:3c, length 46
12:14:26.124996 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:14:28.854572 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:14:31.124977 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:14:31.229352 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:32.227903 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:33.227905 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:35.716741 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
12:14:35.716765 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:14:39.386403 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:40.383902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:41.383902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:44.273257 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:45.271902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:46.271901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:48.386574 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:49.383901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:50.383899 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:50.609189 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
12:14:53.158892 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:14:53.273517 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:54.271901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:55.121034 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:14:55.271897 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
12:14:58.181073 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.105, length 46
12:14:58.181098 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:14:59.125605 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
12:14:59.213315 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
12:14:59.213329 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
12:15:01.119714 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
12:15:01.569495 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
^C
72 packets captured
72 packets received by filter
0 packets dropped by kernel

```
2 things catch my eye:

1. EVEN WITHOUT PING RUNNING IN THE OTHER TERMINAL 11 is repeatedly querying the router at 192.168.1.1.  Why?  And could that cause some sort of "noisy port" issue where the router just starts ignoring 11server?
2. 13 is repeatedly dialing its own number and then getting an answer a bit later.  And 13 is acting a bit strange; it doesn't want to stay connected on SSH.  Any chance that something wrong on 13 could be affecting 11?


I can try restarting the router and showing the same output but thought that I would post this first to see if it gives any clues.

---

### Post by frontrow3 on 2017-12-14
@The Cog, thanks for the help.

Here is the output of both commands just after a ping failure:

ip ne list
```
user@11server:/$ ping 192.168.1.1PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.11 icmp_seq=1 Destination Host Unreachable
From 192.168.1.11 icmp_seq=2 Destination Host Unreachable
From 192.168.1.11 icmp_seq=3 Destination Host Unreachable
From 192.168.1.11 icmp_seq=4 Destination Host Unreachable
From 192.168.1.11 icmp_seq=5 Destination Host Unreachable
From 192.168.1.11 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6000ms
pipe 3

user@11server:/$ ip ne list
192.168.1.1 dev eth0  INCOMPLETE
192.168.1.136 dev eth0 lladdr 00:23:54:fd:47:55 STALE
192.168.1.114 dev eth0 lladdr 60:67:20:f7:9b:3c REACHABLE
192.168.1.103 dev eth0 lladdr 00:21:6a:26:d7:c6 REACHABLE
192.168.1.105 dev eth0 lladdr 00:12:3f:88:3d:0c REACHABLE

```


arp -n
```
user@11server:/$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.11 icmp_seq=2 Destination Host Unreachable
From 192.168.1.11 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 0 received, +2 errors, 100% packet loss, time 3999ms
pipe 2

user@11server:/$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1                      (incomplete)                              eth0
192.168.1.136            ether   00:23:54:fd:47:55   C                     eth0
192.168.1.114            ether   60:67:20:f7:9b:3c   C                     eth0
192.168.1.103            ether   00:21:6a:26:d7:c6   C                     eth0
192.168.1.105            ether   00:12:3f:88:3d:0c   C                     eth0
```

---

### Post by The Cog on 2017-12-14
192.168.1.13 asking for its own address might just be checking to ensure there is no other device with the same address (hoping **not** to get a reply from anything else). I wouldn't expect it to be doing that very often though - is its interface going up and down a lot? I can't see a clear connection between that and your 11server problem though.

Trying to reach the router when you are not pinging is probably normal - the router is the default gateway so it's probably other things like maybe trying to check for security updates. Don't worry about that.

The thing that stands out to me is that the gateway is not answering ARP requests from 11server. Or, at least, any replies it sends are not reaching 11server. I wonder if the ARP requests are reaching the gateway. We can see from 13server that the gateway's MAC address is 50:6a:03:7e:2f:72 (Netgear). I presume (might be worth checking) that **ip nei list** on 11server will show 192.168.1.1 as failed.

At this stage I would probably go to the router to see what is configured there, and what stats are available. I would especially look for any firewall rules or static NAT entries for 192.168.1.11. I might also be tempted to try changing the address of 11server to try to work out whether it's the address .11 that's important or whether the problem stays with the server. 

Have you tried plugging into a different switch port or swapping the cable?

It might be interesting to add a manual ARP entry to 11server for the gateway and see how much that fixes:
```
sudo ip ne add 192.168.1.1 lladdr 50:6a:03:7e:2f:72 dev eth0
```
P.S. Replace "add" wth "del" in the above command to remove the entry again. 
Above command will not survive a reboot, probably not even the interface going down/up.

---

### Post by frontrow3 on 2017-12-14
@The Cog, thanks for the next steps.

Here is the result of ip nei list
```
user@11server:/$ ip nei list192.168.1.144 dev eth0 lladdr c4:1c:ff:cf:f0:9d STALE
192.168.1.1 dev eth0  FAILED
192.168.1.114 dev eth0 lladdr 60:67:20:f7:9b:3c STALE
192.168.1.103 dev eth0 lladdr 00:21:6a:26:d7:c6 DELAY
192.168.1.105 dev eth0 lladdr 00:12:3f:88:3d:0c REACHABLE

```
So, yes, it shows as failed.


For kicks I checked a tcpdump while the router was pinging 11 server and the results are:

```
user@11server:/etc/network$ sudo tcpdump -npe -i eth0 icmp or arptcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
14:06:34.275651 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
14:06:36.265844 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
14:06:49.612508 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
14:06:54.399799 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
14:06:54.399828 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
14:06:58.299988 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
14:06:59.688010 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
14:07:00.262883 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
14:07:03.433716 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:04.431900 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:04.572822 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
14:07:05.431901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:05.775899 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.105 tell 192.168.1.11, length 28
14:07:05.776021 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Reply 192.168.1.105 is-at 00:12:3f:88:3d:0c, length 46
14:07:07.262709 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
14:07:09.686590 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
14:07:12.433926 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:13.431901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:14.431900 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:20.889405 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.136 tell 192.168.1.12, length 46
14:07:22.688593 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:23.687907 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:24.687898 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:25.896025 00:21:6a:26:d7:c6 > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.103, length 46
14:07:25.896046 00:0b:db:94:20:e3 > 00:21:6a:26:d7:c6, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
14:07:30.293089 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
14:07:32.258587 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
14:07:32.417573 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:33.415902 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:34.415901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:34.866891 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Reply 192.168.1.13 is-at 00:12:3f:ec:f0:3a, length 46
14:07:37.258524 00:12:3f:ec:f0:3a > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.13 (ff:ff:ff:ff:ff:ff) tell 192.168.1.13, length 46
14:07:40.074584 00:12:3f:88:3d:0c > 00:0b:db:94:20:e3, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.11 (00:0b:db:94:20:e3) tell 192.168.1.105, length 46
14:07:40.074608 00:0b:db:94:20:e3 > 00:12:3f:88:3d:0c, ethertype ARP (0x0806), length 42: Reply 192.168.1.11 is-at 00:0b:db:94:20:e3, length 28
14:07:41.417802 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:42.415900 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:43.415901 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:49.602382 00:04:23:86:f0:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: Request who-has 192.168.1.121 tell 192.168.1.12, length 46
14:07:53.215125 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
14:07:54.211905 00:0b:db:94:20:e3 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 42: Request who-has 192.168.1.1 tell 192.168.1.11, length 28
^C
40 packets captured
40 packets received by filter
0 packets dropped by kernel

```
The pings from the router are not getting to 11server.


I went through the router menus and there are not any sites nor services blocked.  There are no firewall rules built in except for that.....at least not that I can see.  There is port forwarding set on the router going to .11 for SSH, HTTP, FTP, and an application that uses port 8069.  No access control.  No parental controls set.  192.168.1.11 is shown as attached to the router even though they cannot ping each other (ODD?).    One thing that I am not sure about is that there is a choice under "IPv6" for "Disable IPv6 Firewall Protection" and that is checked.


I can try changing the IP address of 11server in a while at the same time as checking tcpdump right after a router restart but since it will disrupt the network I have to schedule those so will wait until after checking your other suggestions.

At this point I guess i should add some more historical information.  I didn't include it before because I didn't think that it was relevant and didn't want to dump too much info and confuse things.  But maybe it is relevant or will shed some light for you.  Here is some history:
This same thing happened a couple of years ago.  At that time the IP addresses were different and it magically solved itself when I changed the IP address of the "11server".  That led me to change the DHCP and static addresses across the network but to completely do that in all services and places is a lot of work and I couldn't do it all so a bunch of things were left broken.  These included many of the internal-only domain names to our internal-only websites (which were old development versions, so not critical to access anymore) and some hostname resolution issues.  I finally, in the past couple weeks, got time to go back and try to clean everything up.  I updated a bunch of old Bind9 zones to work.  I also changed the local workgroup name because we now have a commercial office in additional to this home office and the commercial office is using the old workgroup name and I am working on setting up a VPN to access the commercial network from the home network (with some problems) and didn't want conflicts due to identical workgroup names.  That was when this problem reappeared.  Everything besides this is working on the home office network now (for the first time in a long while).  So, I am hoping to avoid having to permanently change the IP address of 11server, and thus of the DNS, DHCP, FTP, and other services that it runs, because that is a LOT of work and is what broke the network before.  I have no problem changing the IP as a test but are you saying that it might require changing it permanently?  And if I do will the problem eventually come back again as it has now?  My problems back 2 years ago are described in this post if you think that it may help to review it: [https://superuser.com/questions/993986/ubuntu-14-04-static-ip-server-cannot-ping-router-nor-internet](https://superuser.com/questions/993986/ubuntu-14-04-static-ip-server-cannot-ping-router-nor-internet)


I just tried switching the port on the switch for the cable going to .11 but no affect.

I tried your suggestion of adding a manual ARP entry but no effect.  Output is below:

```
user@11server:~$ sudo ip ne add 192.168.1.1 lladdr 50:6a:03:7e:2f:72 dev eth0
RTNETLINK answers: File exists

user@11server:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.11 icmp_seq=3 Destination Host Unreachable
From 192.168.1.11 icmp_seq=4 Destination Host Unreachable
From 192.168.1.11 icmp_seq=5 Destination Host Unreachable
From 192.168.1.11 icmp_seq=6 Destination Host Unreachable
^C
--- 192.168.1.1 ping statistics ---
8 packets transmitted, 0 received, +4 errors, 100% packet loss, time 6999ms
pipe 3

```

I switched it back


Any other "easy" suggestions before I look into trying to schedule network restart?

---

### Post by frontrow3 on 2017-12-14
@The Cog:

I tried changing the IP address of the 11server port to .14 and the problem went away.  It could then ping the router and the router could ping it back.  I changed it back to .11 and the problem came back.  So, what to do?

When this happened in 2015 the IP address of the "11server" was .100.  Now it was changed to .11 and the problem has come back.  What could be causing this behavior of it deciding that it does not like a certain IP address?  Is there anything that I can flush, restart, or reset that might have some conflicting information stored in it for the 11server MAC address?

---

### Post by The Cog on 2017-12-14
It looks like the path from the router to 11server is losing packets. While you try to ping the server from the router it should receive either ARP requests or if ARP succeeded, ping requests. Your trace shows it received neither.

I assume there is no network tracing capability in the router. At this stage, I would probably try to look at the MAC forwarding table in the switch to make sure it knows the correct port to output packets to the server on. Is it possible to view the forwarding table of the switch? One distant possibility is that something is echoing packets from 11server forming a bridging loop so that the switch keeps seeing 11server on a different port. Is there any possibility that a VPN might be creating such a bridging loop? To a remote site and back? It can't be a local ethernet loop because the resulting broadcast storm at ethernet speed would crash the entire network.

I wonder if the period during which it works after a router reset might be how long it takes for a bridging loop over a VPN to get established.

Then I would try to see if the switch allowed copying the traffic on one port to another port with a sniffer attached so you can trace what's going in and out of the switch.

Beyond that I think I'm out of ideas. I would really want to get packet traces at every step to see exactly who is sending and where in the chain the packets are getting lost. If you can't get the switch to output to a sniffer, I might even want to use a PC with two ethernet ports, set it up to bridge between them and insert it between the switch and the router just to be able to use tcpdump and get a trace of what's really happing at the router.

I'm off to bed now. I'll look to follow up tomorrow.

---

### Post by frontrow3 on 2017-12-14
@The Cog

The router DOES have a traceroute.  Results of traceroute on IPv4 to 192.168.1.11 with:
Max Hops = 32
Data Size (in bytes) = 255
Base Port = 33434
Resolve Host = Yes
Using ICMP = Yes
are:

```
traceroute to 192.168.1.11 (192.168.1.11), 32 hops max, 283 byte packets
 1  96.120.68.245 (96.120.68.245)  20.000 ms  10.000 ms  10.000 ms
 2  *  *  *
 3  *  *  *
 4  *  *  96.120.68.245 (96.120.68.245)  10.000 ms !A
 5  *  *  *
 6  *  *  96.120.68.245 (96.120.68.245)  10.000 ms !A
 7  *  *  *
 8  *  *  *
 9  *  *  *
10  *  *  *
11  *  *  *
12  *  *  *

```

Setting ICMP = No or Resolve Host = No or BOTH do not change the results.

What is that 96.120.68.245 IP address?


Traceroute to another local static IP is fine:

```
traceroute to 192.168.1.12 (192.168.1.12), 32 hops max, 283 byte packets
 1  192.168.1.12 (192.168.1.12)  0.000 ms  0.000 ms  0.000 ms

```


Traceroute to the IPv6 version of the .11 address shows:

```
traceroute to 0:0:0:0:0:ffff:c0a8:10b (::ffff:192.168.1.11) from 2001:558:6017:11f:5c40:9bdf:28f3:24d3, 32 hops max, 283 byte packets
 1traceroute6: sendto: Network is unreachable

```

That makes sense since IPv6 was disabled on the .11 server.


No way to view the MAC forwarding table on the smart switch that I can see.  But since it is sending the ping packets from other hosts to the right address for 11server then wouldn't that be impossible?  There is a VPN client on the PC from which I am SSHing to 11server but it has been off during all this testing.  There is another computer on the network with a different VPN client connecting to a different VPN and that was on for most of this but I just turned it off and disconnected it from the network and nothing is different.


The smart switch does have a Monitor function that allows me to choose a port number "connected to network analyzer" and  "port to be watched".  Is that what you need?  If so, how would I setup the "network analyzer"?  I will try to setup tcpdump the way I THINK it might be supposed to work and see if I can get anything useful.  If I do I will post it here.  If not then I will check you tomorrow.

Get some sleep.  And thanks so much for your help on this.

---

### Post by darkod on 2017-12-15
You don't have any special static routes configured on the router right? Maybe from your VPN setup attempts?

The traceroute shows the router is actually sending traffic destined for .1.11 out to public internet. The first hop is a public IP. No wonder the traffic never reaches the server. After it gets out on the internet 192.168.1.0/24 is lost, it's not routable on public internet.

But on the other hand, traffic for other machines on the LAN is sent correctly. So it seems the router is not making the mistake for the whole 192.168.1.0/24 subnet, just for the .1.11 address. A static route would do that for example...

---

### Post by frontrow3 on 2017-12-15
@Darko, thanks for taking a look.

Yeah, that's what I thought that output meant....that it was sending the traceroute out the WAN side of the router and not the LAN side (right?).  I don't know why it would do that unless that built-in traceroute is ONLY for pinging the WAN side.  But, no, because it traceroutes 192.168.1.12 correctly in 1 hop.

As far as static routes I don't think so.  I don't even think that the router allows me to input a static route.  I know I can, and have, entered 4 port forwards for different services to .11 but that is different, right?  What would a static route look like?  What woudl it be called and under what heading?  The router is all web-based graphical setup.  Then again, maybe that is the problem.  How can I find it if it exists?

---

### Post by The Cog on 2017-12-15
Well that was unexpected. 
> No way to view the MAC forwarding table on the smart switch that I can see. But since it is sending the ping packets from other hosts to the right address for 11server then wouldn't that be impossible? 
Doh! You are right. So it really looks like it's the router that's the origin of the problem. But to be really, really sure, I would do another tcpdump (on 11server) while pinging from another PC, and compare the MAC addresses in the trace to the MAC addresses in the machine's ifconfig to try to eliminate the possibility of a "man in the middle".

Apparently the C6300 cannot support static routes.  I found a manual and see that there is no way to view the routing table (WTF?). 

96.120.68.245 is a Comcast owned address. Interestingly, that comcast address shows up at several different hop counts: Routing loop withing comcast? !A apparently means administratively prohibited - probably from a firewall. 

Is there any config anywhere that might suggest why .11 should be treated differently to any other local address? I wouldn't have expected the port forwarding config to have anything to do with it, but as odd things are happening I can't be sure. Is there a default DMS server configured?

Right now all I can say is the router is doing strange things and I don't trust it. Make sure remote management is disabled. Maybe restore factory settings and then reconfigure it. Maybe re-flash it too.

---

### Post by frontrow3 on 2017-12-15
@The Cog

Could it have something to do with Comcast trying to force DNS server lookups to be via IPv6 when much of my network is not configured for v6?  I have set my DNS servers with IPv4 addresses in the router and on various machines but am getting a couple of IPv6 addresses added to the end of the list of DNS servers when I do a ifconfig.  Comcast must be adding these when the router (which is also the cable modem) boots and gets its external IP address via DHCP from Comcast.

OR, could Comcast be setting the router so that it wants to resolve DNS via external servers but we have an internal DNS server and that is confusing it?  I will tell you that Comcast downloads its own firmware on the router automatically which changes teh interface a bit and even removes the screen where firmware can be flashed manually.  I fear Comcast is setting a lot of internal settings automatically that we cannot even see.

I cannot see any reason why the .11 address would be treated as an external address........but, then again, I fear that there may be settings that are not visible.

What is a DMS server?  You mean DNS?

---

### Post by The Cog on 2017-12-15
I don't think it's anything to do with DNS. You are only dealing with IP addresses here - no names, so no need for name lookups.

---

### Post by The Cog on 2017-12-15
> What is a DMS server? You mean DNS? 
No, sorry, I meant DMZ server. Thought I can't see any reason why that might cause your problem either.

I don't think it's anything to do with DNS. You are only dealing with IP addresses here - no names, so no need for name lookups.

Perhaps you should have a moan at Comcast if you know they meddle with your router. But having read a few user opinions about Comcast, I guess that's not a useful suggestion.

---

### Post by frontrow3 on 2017-12-17
@The Cog

Thanks for the suggestions.

No DMZ on this network.

Why did you suggest disabling remote management and resetting to factory settings?  Are you thinking it may have been hacked?

---

### Post by The Cog on 2017-12-17
It did go through my mind that you may have been hacked which is why I made those suggestions. But actually I think it's unlikely because any decent hack would not disable things so that they need investigating - a good hack would be un-noticable, undetectable.

Resetting to factory defaults and reconfiguring from there will flush out any overlooked config changes or config errors that somehow got saved as a result of bugs in the configuration editing code. Not saying there are either software bugs or config errors, just that starting from a clean config just might fix it. There is something that we don't understand going on in the router and I am clutching at straws.

---

### Post by frontrow3 on 2017-12-18
OK, thanks for the help.  I am going to try to find a time to do the reset and enter all the settings again.

BTW, I did lookup online and find that a couple of months ago a huge security vulnerability was identified in this modem/router and 30 other Netgear models.  It allowed an outside attacker to gain admin access quite easily.  It has since been patched on this one but it could have been compromised before the patch.  Still, as you say, it just doesn't act that way.  I am leaning more toward a bad software update or Comcast firmware defects as the cause.

---

### Post by frontrow3 on 2017-12-23
Finally got a chance to factory reset the router.  No difference.

11server still cannot ping the router/default gateway nor Internet IP addresses and gets "Destination Host Unreachable" but it can ping and be pinged by other IP addresses on the local network.  The router cannot ping 11server but can ping other IP addresses on the local network and Internet.  All other local network hosts can ping 11server, each other, and the Internet just fine.  The only thing that seems to be broken is the communication channel between 11 server and the router/primary gateway.

Called Comcast to troubleshoot.  As expected got a script-reading flunkie.  Not sure he ever got to the point where he even knew what he was supposed to be looking for.  He did tell me they cannot see the routing table in the router either.  At least it got escalated up to level 2 support and they are supposed to do something within 12 to 24 hours so maybe they have a clue and more access.  I will let you know.

---

### Post by frontrow3 on 2018-01-03
@The Cog: So I finally had to call Comcast back (they never called me as promised) and got Level 2 support who told me they could see nothing inside my router.  They said I had to call Netgear and they could see inside my router.  Netgear needs to verify my sales receipt to see if I qualify for support so no help there either.

I did find one hint that made me download the Netgear Genie app, which basically is an app that accesses the settings on the modem/router without going through the web browser interface.  The thing is that it shows certain screens that are missing from the browser menu structure.  One is the network map, which was removed when Comcast pushed their firmware onto my modem/router.  Another is a better set of diagnostic tools.  So, I tried pinging the .11server using the ping in the Netgear Genie and IT WORKS....sort of.  If I ping the NetBIOS name of .11server then it works fine:
  Reply from 192.168.1.11: bytes=32 time=3ms TTL=64
  Reply from 192.168.1.11: bytes=32 time=3ms TTL=64
  Reply from 192.168.1.11: bytes=32 time=4ms TTL=64
  Reply from 192.168.1.11: bytes=32 time=4ms TTL=64


  Finished
If I ping the IP address 192.168.1.11 then it sort of works but then says it does not:
  Reply from 192.168.1.11: bytes=32 time=3ms TTL=64
  Reply from 192.168.1.11: bytes=32 time=4ms TTL=64
  Reply from 192.168.1.11: bytes=3 time=2ms TTL=4
  Reply from 192.168.1.11: bytes=32 time=3ms TTL=64
  Ping request could not find host 192.168.1.11. Please check the name and try again.
  Request timed out


  Finished
Huh?  It gets 4 replies from .11 but then says it could not find host.  Am I missing something or is this absurd?

I still get failure when trying to ping the IP address of .11server from the browser menu interface of the modem/router.  That seems really odd; the modem/router can ping .11server when using the app but not when using the browser interface?

I still get failure when trying to ping the IP address or NetBIOS name of the modem/router from .11server.

In the "network map", which shows a star diagram of the devices connected, .11server shows up and is correctly identified.  I still do not see a way to access anything that looks like a real routing table to see if there is a static route stuck in there.

Any ideas?

---

