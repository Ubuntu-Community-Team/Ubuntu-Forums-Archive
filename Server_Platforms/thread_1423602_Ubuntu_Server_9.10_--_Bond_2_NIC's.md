---
title: "Ubuntu Server 9.10 -- Bond 2 NIC's"
date: 2010-03-06
forum: Server Platforms
---

### Post by dasunsrule32 on 2010-03-06
I would like to do a couple of things, I am running a Dell Poweredge 2850 and want to bond the two NIC's. I was looking [here]("https://help.ubuntu.com/community/LinkAggregation") to do the bonding. It get's a little more tricky with what I want to do from here, I need to two virtual adapters on top of the bond: one at IP 192.168.56.2 and 192.168.56.3. I am binding SSH to the first IP.

Is it possible that I do this config over SSH? It may be asking a lot to do this, but since I have SSH already configured to bind to 192.168.56.2, if I put the config together (assuming it is correct), it should work after restarting the networking service. If anyone could shed some ideas on this and how to accomplish this, it would be awesome! Thank you!

---

### Post by KiLaHuRtZ on 2010-03-06
Check out my post here...

[http://ubuntuforums.org/showpost.php?p=8763893&postcount=3]("http://ubuntuforums.org/showpost.php?p=8763893&postcount=3")

Although, your 'interfaces' file would look like this...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 192.168.56.2
netmask [SUBNET MASK]
gateway [DEFAULT ROUTER]
network [NETWORK ADDRESS]
broadcast [BROADCAST ADDRESS]
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

# The secondary network interface
auto bond0:0
iface bond0:0 inet static
address 192.168.56.3
netmask [SUBNET MASK]
network [NETWORK ADDRESS]
broadcast [BROADCAST ADDRESS]
```

You can add as many secondaries as you need...

bond0:1
bond0:2
bond0:3
etc...

---

### Post by dasunsrule32 on 2010-03-06
Thanks, I will take a look at this later in the week. I will let you know how it goes.

---

### Post by NullHead on 2010-03-06
I run a bonded setup just like this. It works well with the method outlined by KiLaHuRtZ.

---

### Post by dasunsrule32 on 2010-03-06
> **NullHead said:**
> I run a bonded setup just like this. It works well with the method outlined by KiLaHuRtZ.

I am going for it over SSH, I will let you know if I lock myself out or not. :P

---

### Post by dasunsrule32 on 2010-03-06
I want to basically provide more bandwith to the server? Is this going to do what I need? Thanks!

Is the the correct line for /etc/modules?
```

bonding mode=active-backup miimon=100 primary=eth0

```

Is this the correct setup for my config I will be using below:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 192.168.56.2
netmask 255.255.255.0
gateway 192.168.56.1
dns-nameservers 192.168.56.89
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

# The secondary network interface
auto bond0:0
iface bond0:0 inet static
address 192.168.56.3
netmask 255.255.255.0

```

---

### Post by KiLaHuRtZ on 2010-03-06
Use this...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 192.168.56.2
netmask 255.255.255.0
gateway 192.168.56.1
network 192.168.56.0
broadcast 192.168.56.255
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

# The secondary network interface
auto bond0:0
iface bond0:0 inet static
address 192.168.56.3
netmask 255.255.255.0
network 192.168.56.0
broadcast 192.168.56.255
```

Place your nameservers in '/etc/resolv.conf'...

```
nameserver 192.168.56.89
```

---

### Post by KiLaHuRtZ on 2010-03-06
> **dasunsrule32 said:**
> I want to basically provide more bandwith to the server? Is this going to do what I need? Thanks!

Is the the correct line for /etc/modules?
```

bonding mode=active-backup miimon=100 primary=eth0

```

This will not provide more bandwidth, just fault tolerance.  If you want more bandwidth, you need to do the 802.3ad mode.  However, you switch needs to support 802.3ad to work.

---

### Post by dasunsrule32 on 2010-03-06
I have two Dell Powerconnect 3024's, they support Link Aggregation aka Port Trunking. Would my /etc/interfaces file end up changing at all or would /etc/modules be the only config changing?

EDIT: This is how my /etc/modules looks now, if it isn't correct, please let me know. Thanks!

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
rtc

# mode=0 (balance-rr), mode=1 (active-backup), mode=2 (balance-xor), mode=3 (broadcast), mode=4 (802.3ad), mode=5 (balance-tlb), mode=6 (balance-alb)
bonding mode=4 miimon=100

```

---

### Post by KiLaHuRtZ on 2010-03-07
That should work, but you might wish to have a look at this...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419")

---

### Post by dasunsrule32 on 2010-03-08
> **KiLaHuRtZ said:**
> That should work, but you might wish to have a look at this...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/482419)

Thanks, that would've been ugly for my SSH attempt. I will install the latest package for ifenslave, that should take care of the issue with bonding in Karmic.

---

### Post by dasunsrule32 on 2010-03-08
Ok, so I did it successfully over SSH! :p How can I verify that all is working as it should? My ifconfig does show that has the bond0 and bond0:0 interfaces are working, I can ping them and access my vm's via VMWare. Thanks!

Here is my ifconfig:

```

bond0     Link encap:Ethernet  HWaddr 00:14:22:22:12:22
          inet addr:192.168.56.2  Bcast:192.168.56.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe22:1222/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:12566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2371585 (2.3 MB)  TX bytes:3373566 (3.3 MB)

bond0:0   Link encap:Ethernet  HWaddr 00:14:22:22:12:22
          inet addr:192.168.56.3  Bcast:192.168.56.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:14:22:22:12:22
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:11131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9910 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2150015 (2.1 MB)  TX bytes:3366250 (3.3 MB)

eth1      Link encap:Ethernet  HWaddr 00:14:22:22:12:22
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1435 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:221570 (221.5 KB)  TX bytes:7316 (7.3 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2830351 (2.8 MB)  TX bytes:2830351 (2.8 MB)

```

---

### Post by KiLaHuRtZ on 2010-03-08
```
cat /proc/net/bonding/bond0
```

---

### Post by dasunsrule32 on 2010-03-08
This is what I got from the output, does all seem well? Thanks!

```

Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: slow
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
        Aggregator ID: 1
        Number of ports: 1
        Actor Key: 17
        Partner Key: 1
        Partner Mac Address: 00:00:00:00:00:00

Slave Interface: eth0
MII Status: up
Link Failure Count: 2
Permanent HW addr: 00:14:22:22:12:22
Aggregator ID: 1

Slave Interface: eth1
MII Status: up
Link Failure Count: 2
Permanent HW addr: 00:14:22:22:12:23
Aggregator ID: 2

```

---

### Post by NullHead on 2010-03-08
You can use an app called "bmon" to monitor each network device's throughput. That will tell you if it's working or not.

---

### Post by dasunsrule32 on 2010-03-08
> **NullHead said:**
> You can use an app called "bmon" to monitor each network device's throughput. That will tell you if it's working or not.

Perfect, let me give that a whirl. Thanks! I love learning something new each day! Thanks for the help!

---

### Post by dasunsrule32 on 2010-03-09
I am marking as solved, thank you for the help. I put a simple how-to together on my site, if anyone wants to post it in the forums, feel free. Just ask that you credit the three involved in this post with the credit for it. Thanks.

See it [here]("http://www.christiantechsaz.com/viewtopic.php?pid=150#p150").

---

### Post by NinjaTTT on 2011-05-12
Just to remind...
I'm also setting interface bonding and tried out 802.3ad mode on Ubuntu 10.0.4 LTS server.
But without the switch supporting dynamic linking it's not really balanced?!
Some links to read about it on
[http://lists.us.dell.com/pipermail/linux-poweredge/2007-March/029906.html]("http://lists.us.dell.com/pipermail/linux-poweredge/2007-March/029906.html")
[http://backdrift.org/howtonetworkbonding]("http://backdrift.org/howtonetworkbonding")
and if I'm corrent in your "cat /proc/net/bonding/bond0" both slave devices should have same aggregator ID...


> **dasunsrule32 said:**
> This is what I got from the output, does all seem well? Thanks!

```

Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: slow
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
        Aggregator ID: 1
        Number of ports: 1
        Actor Key: 17
        Partner Key: 1
        Partner Mac Address: 00:00:00:00:00:00

Slave Interface: eth0
MII Status: up
Link Failure Count: 2
Permanent HW addr: 00:14:22:22:12:22
Aggregator ID: 1

Slave Interface: eth1
MII Status: up
Link Failure Count: 2
Permanent HW addr: 00:14:22:22:12:23
Aggregator ID: 2

```

---

