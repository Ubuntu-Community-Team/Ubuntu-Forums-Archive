---
title: "Why isn't UFW blocking Heartbeat broadcast messages"
date: 2014-02-25
forum: Security
---

### Post by kevpatts2 on 2014-02-25
Okay, so I have been having trouble with setting up separate heartbeats on 2 different but partially overlapping subnets and the problem I have found is that UFW isn't blocking heartbeats broadcast messages even though I've set it to.

The two subnets are 10.4.10.X and 10.4.20.X. Each has a broadcast address of 10.2.255.255 (I know this makes them overlap but they have to for other reasons). I then set the UFW rule to:
```
sudo ifconfig bond0 && sudo ufw verbose && sudo tcpdump -n dst port 694
bond0     Link encap:Ethernet  HWaddr
          inet addr:10.4.20.1  Bcast:10.4.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:36916659 errors:0 dropped:17713819 overruns:0 frame:0
          TX packets:48639758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7543490390 (7.5 GB)  TX bytes:4787636845 (4.7 GB)

Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
694                        ALLOW       10.4.20.0/24
22                         ALLOW       Anywhere (v6)

tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
04:53:50.082434 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 219
04:53:51.556127 IP 10.4.20.1.52758 > 10.4.255.255.694: UDP, length 226
04:53:51.599159 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 231
04:53:51.599173 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 220
04:53:51.603112 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 231
04:53:52.083533 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 219
04:53:53.556939 IP 10.4.20.1.52758 > 10.4.255.255.694: UDP, length 226
04:53:53.600198 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 220
04:53:54.084427 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 219
04:53:55.557868 IP 10.4.20.1.52758 > 10.4.255.255.694: UDP, length 226
04:53:55.601079 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 220
04:53:56.075402 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 219
04:53:56.341478 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 231
04:53:57.558591 IP 10.4.20.1.52758 > 10.4.255.255.694: UDP, length 226
04:53:57.602124 IP 10.4.10.2.43009 > 10.4.255.255.694: UDP, length 220
04:53:58.076366 IP 10.4.10.1.59813 > 10.4.255.255.694: UDP, length 219
^C
16 packets captured
16 packets received by filter
0 packets dropped by kernel
21 packets dropped by interface
```

Why are the packets from 10.4.10.1 and 10.4.10.2 not being blocked by UFW?

---

### Post by Doug S on 2014-02-25
tcpdump is capturing and displaying the packet before it is delivered to the iptables rule set that results from UFW. tcpdump is not telling you what happens to the packet after it arrives at the network interfaces. I would suggest adding some logging to your UFW stuff or the resulting iptables rule set to determine what is going on.

---

