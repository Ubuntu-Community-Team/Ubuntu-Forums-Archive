---
title: "[solved] Source IP issue with keepalived and multiple IPs on a single interface"
date: 2011-03-27
forum: Server Platforms
---

### Post by kihjin on 2011-03-27
*All real IPs for my servers have been replaced by 123.123.123.* *

**Solution is at the end**

Last night I setup a keepalived configuration that seems to work well so far. The keepalived master node has two IP addresses:

```
root@:~# ip addr
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:xx:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 123.123.123.200/24 brd 123.123.123.255 scope global eth0
    inet 123.123.123.123/24 brd 123.123.123.255 scope global secondary eth0:0
    inet6 fe80::230:67ff:fe62:957/64 scope link 
       valid_lft forever preferred_lft forever
```

The address "123.123.123.200" is the machine's primary address. The address "123.123.123.123" is used for routing traffic on **all ports** to a set of 7 front end servers.

This morning, I logged onto the master keepalived node and tried to install a package using apt-get. It failed to connect to the repository. Further investigation revealed that I cannot receive data from servers outside of my network - but only on that server. 

```
root@:~# wget google.com
--2011-03-27 14:07:39--  http://google.com/
Resolving google.com... 74.125.225.17, 74.125.225.19, 74.125.225.18, ...
Connecting to google.com|74.125.225.17|:80... ^C

```

Just hangs. Ping still works:

```
root@:~# ping google.com
PING google.com (74.125.225.20) 56(84) bytes of data.
64 bytes from 74.125.225.20: icmp_seq=1 ttl=56 time=1.41 ms
64 bytes from 74.125.225.20: icmp_seq=2 ttl=56 time=1.72 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1006ms
rtt min/avg/max/mdev = 1.414/1.571/1.728/0.157 ms

```

tcpdump during the above wget seems to reveal that packets are leaving, but not coming back:

```
root@:~# tcpdump host 74.125.225.20
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
14:11:30.683733 IP 123.123.123.123.48682 > 74.125.225.20.www: Flags [S], seq 137934342, win 5840, options [mss 1460,sackOK,TS val 405978525 ecr 0,nop,wscale 7], length 0
14:11:30.685152 IP 74.125.225.20.www > 123.123.123.123.48682: Flags [S.], seq 1121921204, ack 137934343, win 5672, options [mss 1430,sackOK,TS val 1320933460 ecr 405978525,nop,wscale 6], length 0
14:11:30.685171 IP 74.125.225.20.www > 123.123.123.123.48682: Flags [S.], seq 1121921204, ack 137934343, win 5672, options [mss 1430,sackOK,TS val 1320933460 ecr 405978525,nop,wscale 6], length 0
14:11:31.046280 IP 74.125.225.20.www > 123.123.123.123.48682: Flags [S.], seq 1121921204, ack 137934343, win 5672, options [mss 1430,sackOK,TS val 1320933821 ecr 405978525,nop,wscale 6], length 0
```

It looks like the machine is deciding to use the secondary address for external communication. 

**Solution**

I found the solution while typing up my post, so I figured I would post anyway, should it help anyone out in the future. 

```
root@:~# ip route
123.123.123.0/24 dev eth0  proto kernel  scope link  src 123.123.123.200 
default via 123.123.123.1 dev eth0  src 123.123.123.123  metric 100 
default via 123.123.123.1 dev eth0  metric 100 
```

This explains all of the above. Routing works for local servers, but for everything else, it tries to use "123.123.123.123" as a source address. I was able to fix this by doing the following:

ip route change default via 123.123.123.1 dev eth0  src 123.123.123.200

This seems to force outgoing routes to use 123.123.123.200 as a source address and therefore return packets aren't routed out somewhere else.

Now to figure out how to make this permanent in /etc/network/interfaces ...

---

