---
title: "High ping/latency on Xen box"
date: 2013-12-15
forum: Virtualisation
---

### Post by apitcraft on 2013-12-15
I am having problems with my Xen box. Once in a while it has too high ping/latency and it is very annoying.
It does not matter if I am pinging server from outer network (LAN0) or inner network (LAN1), high ping is for both of lines.

P.S. Without Xen everything is running smoothly.
P.P.S. I had the same problem with another box running Xen, but somehow the problem disappeared.

About configuration:

```

     LAN0                LAN1
      |                   |
+-----+-------------------+--+
|     |                   |  |
| +---+---------------+   |  |
| |   |               |   |  |
| | eth0    xenbr0    | eth1 |
| |                   |   |  |
| |    vif1.0         |   |  |
| |      |            |   |  |
| +------+------------+   |  |
|        |                |  |
| +------+----------+     |  |
| |      |          |     |  |
| |     eth0        |     |  |
| |      |          |     |  |
| |  +-+-+---+---+  |     |  |
| |  |   |   |   |  |     |  | 
| | www ssh ftp pop |    ssh |
| |                 |        |
| |     Domain1     | Domain0|
+-+-----------------+--------+

```

Sometimes there are many packets with high ping in a row.[COLOR=#333333][FONT=Helvetica Neue]
 [IMG]http://i.stack.imgur.com/Ul8tu.png[/IMG][/FONT][/COLOR]
Sometimes there is only one high ping packet in a minute or so.[COLOR=#333333][FONT=Helvetica Neue]
 [IMG]http://i.stack.imgur.com/ADgdl.png[/IMG]

[/FONT][/COLOR]xm info
```

host                   : serverX
release                : 3.5.0-23-generic
version                : #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013
machine                : x86_64

```

Hopefully someone can help me.

---

### Post by tgalati4 on 2013-12-15
What are the loads on this server?  Without that it is speculation.  If loads are consistently low, then there could be a xen/kernel/swapping problem.  If loads are peaky and high, then latency should reflect that.

Run *xload* if you have a graphics server or *htop* and post a few screen shots.  Examine the RAM with *free*; if you are out of RAM (due to a leaky application) then swapping will slow things down.  This will sometimes clear itself, sometimes not.

What is the hardware?  Toasters generally have high latency.

---

### Post by apitcraft on 2013-12-15
Domain0: xm top
```

xentop - 18:03:17   Xen 4.1.2
2 domains: 1 running, 1 blocked, 0 paused, 0 crashed, 0 dying, 0 shutdown
Mem: 33548272k total, 32870172k used, 678100k free    CPUs: 8 @ 2992MHz
      NAME  STATE   CPU(sec) CPU(%)     MEM(k) MEM(%)  MAXMEM(k) MAXMEM(%) VCPUS NETS NETTX(k) NETRX(k) VBDS   VBD_OO   VBD_RD   VBD_WR  VBD_RSECT  VBD_WSECT SSID
  Domain-0 -----r     161513    0.0    1048576    3.1   no limit       n/a     8    0        0        0    0        0        0        0          0          0    0
  virtual1 --b---     128529    0.0   31457280   93.8   31457280      93.8     8    1  7604726 17270964    2        0   181258  3374788    7781018   69690752    0

```

Domain0: free
```

             total       used       free     shared    buffers     cached
Mem:        761672     597856     163816          0      45732     286656
-/+ buffers/cache:     265468     496204
Swap:      7811068      22636    7788432

```


Domain0: htop
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248623&d=1387123726[/IMG]

Does anyone else running Xen 4.1.2 is having such problem?

P.S. Dom0 and guest are running on separate disks.

---

### Post by tgalati4 on 2013-12-15
Well, you are not running a toaster that is for sure.  Eight cores and nothing is loaded.  I would post a bug against 4.1.2 and see if others are having problems.

Your original post has screen shots that distinctly look like they are coming from a Windows box.  Perhaps the latency is coming from the Windows networking stack?  Try pinging from a bare metal linux machine to isolate the ping behavior from the client type.  You would not want to confound a linux problem with a Windows problem.  

A Haiku for good measure:

Slow ping on Xen guest?
RAM and load not a problem.
What could be the cause?

---

### Post by apitcraft on 2013-12-17
It does not matter if I am pinging from windows box or linux. Result is the same.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=248664&d=1387262379[/IMG]

High ping is on both - Xen host and Xen guest.

---

### Post by tgalati4 on 2013-12-17
What is the network card on this machine?  Perhaps it is a module problem.

```
sudo lshw -class network
```

Check the cabling--try replacing the network cable and reseating connections.  Change router ports.

---

### Post by apitcraft on 2013-12-17
sudo lshw -class network```

  *-network:0
       description: Ethernet interface
       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: MAC
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.0-0 ip=xx.xx.xx.x latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:122 memory:98820000-9883ffff memory:98400000-987fffff ioport:2020(size=32)
  *-network:1
       description: Ethernet interface
       product: 80003ES2LAN Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:06:00.1
       logical name: eth1
       version: 01
       serial: MAC2
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=1.0-0 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:123 memory:98800000-9881ffff memory:98000000-983fffff ioport:2000(size=32)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vif12.0
       serial: fe:ff:ff:ff:ff:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=vif link=yes multicast=yes

```

As I said before, without Xen everything worked ok, unfortunately it was in different data center, BUT I have already had exactly the same problem on another server, but it [the problem] somehow disappeared.

I already have 2 different LAN cables from the same switch (I guess) to eth0 and eth1 port to the server. For example, another server which is running without Xen in the same rack and same switch (I guess) has no problems at all.

---

### Post by tgalati4 on 2013-12-17
It appears that both of your network cards are running at 100 mbits/sec even though they are 1Gbit/sec rated.  I would presume that the data center has gigabit switches.  So, I would break out my cabling meter and check the bandwidth of the infrastructure wiring.  I was at a job site where 50% of the Cat6 wiring (~400 out of 800 lines) did not pass Cat6 specification.  The crimps looked like they were done by a drunk, colorblind, electrician.

The other thing to check is Quality of Service (QoS).  It's possible that the router has some policies set on the ports that you are using that cause hiccups.  The phone calls must get through.

Expert opinion?
One test is worth a thousand.
What are you waiting for?

---

