---
title: "Hetzner packet loss / Ubuntu network configuration"
date: 2019-11-13
forum: Server Platforms
---

### Post by pjoo on 2019-11-13
Hello,
I just bought an dedicated server on hetzner, and I have issue with packet loss. I didn't change any network settings, so it's probably theier, or ubuntu's default network settings. I never had such issue so I don't know what to do. If you have some idea what I can do to fix this issue, please help. Hetzner support says it's software related, and they won't help.

Here is ping from my house -> hetzner dedicated:
[COLOR=#1D2129][FONT=Consolas]Packets: Sent = 500, Received = 483, Lost = 17 (3% loss),
Approximate round trip times in milli-seconds:
Minimum = 49ms, Maximum = 240ms, Average = 52ms[/FONT][/FONT][/COLOR]



My first server is in OVH. Here is mtr OVH <-> Hetzner. I really need this connection to work.

Hetzner -> OVH:
```
mtr -s 1000 -r -c 1000 yyy.yyy.yyy.yyy
Start: 2019-11-13T18:05:34+0100
HOST: Crafted2                    Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- xxx.xxx.xxx.xxx              1.3%   542    0.3   0.4   0.2  10.3   0.9
  2.|-- 213.239.203.145            1.3%   542    0.4   3.8   0.3 144.5  13.6
  3.|-- 213.239.224.254            1.5%   542    4.9  10.8   4.8 113.3  13.1
  4.|-- 213.239.224.221            1.5%   542    5.2   9.1   5.1  97.6  11.9
  5.|-- 94.23.122.250              1.5%   542    5.8   6.4   5.3  30.6   3.5
  6.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
  7.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
  8.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
  9.|-- 213.186.32.212             1.5%   542   14.3  15.2  14.1  53.2   4.3
10.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
11.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
12.|-- ???                       100.0   542    0.0   0.0   0.0   0.0   0.0
13.|-- yyy.yyy.yyy.yyy            1.5%   542   13.5  13.4  13.4  15.3   0.1

```


OVH -> Hetzner:
```
mtr -s 1000 -r -c 1000 xxx.xxx.xxx.xxx
Start: Wed Nov 13 18:00:28 2019
HOST: ns3084513                   Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- yyy.yyy.yyy.yyy            0.0%  1000    0.3   0.3   0.3  26.6   1.1
  2.|-- 10.17.145.8                0.0%  1000    0.6   0.4   0.4   2.5   0.1
  3.|-- 10.73.0.42                 0.0%  1000    0.2   0.2   0.1   4.1   0.2
  4.|-- 10.95.33.10                0.0%  1000    1.4   4.1   0.7 111.0  11.8
  5.|-- fra-fr5-sbb2-nc5.de.eu     0.0%  1000    8.9   8.9   8.6  16.4   0.3
  6.|-- 10.200.0.6                 0.0%  1000    8.8  10.0   8.6  73.1   4.7
  7.|-- ???                       100.0  1000    0.0   0.0   0.0   0.0   0.0
  8.|-- core5.fra.hetzner.com      0.0%  1000    8.8  12.7   8.8 140.8  13.0
  9.|-- core24.fsn1.hetzner.com    0.0%  1000   13.5  14.1  13.4  74.7   3.7
 10.|-- ex9k1.dc11.fsn1.hetzner.c  0.0%  1000   13.6  14.5  13.4 298.2  13.5
 11.|-- static.xxx.xxx.xxx.xxx.cli  9.4%  1000   13.4  13.4  13.3  15.9   0.1

```

---

### Post by darkod on 2019-11-13
Do you actually have problems with some application or you rely only on ping measurements?

I ask because all those ??? hops in Hetzner -> OVH might mean that the test traffic is not allowed. Or that there is problem with routing the traffic.

Either way, Hetzner might be right (sort of). If those ??? in between are the ones losing packets, it is not responsibility of either Hetzner or OVH.

On other hand, a 3% or similar of lost ping might not be big issue, depending on your application and what sort of connectivity you depend on. This is why I asked if you actually have app issues or not. Maybe the connection is still good enough for your app to work.

---

### Post by The Cog on 2019-11-13
It looks to me as though all the packet loss is on the link between crafted2 and its next hop. From crafted's point of view, everything is giving 1.3-1.5% loss, suggesting no significant loss beyond the first hop. From ns3084513's point of view there is no loss at all until the final destination, supporting the idea that it's all in that last hop. Ignoring the hops that choose not to respond with ttl exceeded messages.

---

### Post by LHammonds on 2019-11-14
If you have something that requires "no packet fragmentation" and the path between source and destination have different MTU sizes, that could cause significant slowdown in bandwidth.

[https://documentation.meraki.com/zGeneral_Administration/Tools_and_Troubleshooting/Troubleshooting_MTU_Issues](https://documentation.meraki.com/zGeneral_Administration/Tools_and_Troubleshooting/Troubleshooting_MTU_Issues)

LHammonds

---

### Post by pjoo on 2019-11-16
Thanks for all response. That issue turned out to be happening, because CPU was overheating, and it was throttling really violently. Everytime cpu overheated, server started loosing packets. Cpu temp got normal -> no packet loss. After some arguing with support, they did change thermal compound, and added additional fan. Now server stopped overheating. 
But there was packet loss again with higher load. Now in kernel.log there is info that network card randomly stops working. It happens quite frequently.

Here is log sample:
```
Nov 16 13:33:09 Debian-101-buster-64-minimal kernel: [159109.607761] e1000e 0000:00:1f.6 eno1: Reset adapter unexpectedlyNov 16 13:33:12 Debian-101-buster-64-minimal kernel: [159112.946082] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 16 13:48:36 Debian-101-buster-64-minimal kernel: [160036.581238] e1000e 0000:00:1f.6 eno1: Reset adapter unexpectedly
Nov 16 13:48:40 Debian-101-buster-64-minimal kernel: [160040.979557] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 16 13:50:37 Debian-101-buster-64-minimal kernel: [160157.668915] e1000e 0000:00:1f.6 eno1: Reset adapter unexpectedly
Nov 16 13:50:41 Debian-101-buster-64-minimal kernel: [160161.467258] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 16 13:54:38 Debian-101-buster-64-minimal kernel: [160398.564270] e1000e 0000:00:1f.6 eno1: Reset adapter unexpectedly
Nov 16 13:54:41 Debian-101-buster-64-minimal kernel: [160401.918586] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
Nov 16 14:09:47 Debian-101-buster-64-minimal kernel: [161307.617873] e1000e 0000:00:1f.6 eno1: Reset adapter unexpectedly
Nov 16 14:09:51 Debian-101-buster-64-minimal kernel: [161311.848114] e1000e: eno1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx

```

I followed their guide [https://wiki.hetzner.de/index.php/Low_performance_with_Intel_i218/i219_NIC/en](https://wiki.hetzner.de/index.php/Low_performance_with_Intel_i218/i219_NIC/en) . But I have kernel version 4.19.0-6, so it should be fixed already. I also tried workaround, but it didn't do anything. Do you have any idea what I can do about that?

---

### Post by pjoo on 2019-11-24
I have to add that I tried installing newest intel e1000e driver (for i219 network card), and still the same issue. I tried both debian and ubuntu (sticked to ubuntu in end), and still the same error. I tried version 18.04 and 19.10. 

I feel hopeless to that issue. I don't know what else I can do o fix it.

---

