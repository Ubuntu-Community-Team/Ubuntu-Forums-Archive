---
title: "High pings and slow transfers on 14.04 LTS"
date: 2015-05-24
forum: Server Platforms
---

### Post by Perf2711 on 2015-05-24
Hello,

I've got a irritating problem. Computer with Ubuntu Server installed on it has very high RTT's, even in local network.
Transfer rates are also low. I have already disabled IPv6.

```
64 bytes from 192.168.0.123: icmp_seq=2 ttl=128 time=98.0 ms
64 bytes from 192.168.0.123: icmp_seq=3 ttl=128 time=97.9 ms
64 bytes from 192.168.0.123: icmp_seq=4 ttl=128 time=97.9 ms
64 bytes from 192.168.0.123: icmp_seq=5 ttl=128 time=97.9 ms
64 bytes from 192.168.0.123: icmp_seq=6 ttl=128 time=97.9 ms
```

Normal ping rates (from other computer, in the same network):
```
64 bytes from 192.168.0.123: icmp_seq=1 ttl=128 time=0.592 ms
64 bytes from 192.168.0.123: icmp_seq=2 ttl=128 time=0.176 ms
64 bytes from 192.168.0.123: icmp_seq=3 ttl=128 time=0.181 ms
64 bytes from 192.168.0.123: icmp_seq=4 ttl=128 time=0.200 ms
```


The kernel version is:
```
Linux eGroupWare 3.16.0-37-generic #51~14.04.1-Ubuntu SMP Wed May 6 15:23:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

My ethernet card is a TP-Link Gigabit card with this chip:
```
04:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8169/8110 Family PCI Gigabit Ethernet NIC
```

Is it something wrong with Realtek? Because the other computer with the same system (different kernel, though) with Qualcomm Atheros card is just fine.

---

### Post by Doug S on 2015-05-26
Hi and welcome to Ubuntu forums,

I don't think it is the NIC. I have the same, or similar card, and get O.K. local ping times:```
doug@s10:~$ ping smythies.com
PING smythies.com (192.168.111.1) 56(84) bytes of data.
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=1 ttl=64 time=0.118 ms
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=2 ttl=64 time=0.111 ms
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=3 ttl=64 time=0.111 ms
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=4 ttl=64 time=0.117 ms
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=5 ttl=64 time=0.111 ms
64 bytes from ns1.smythies.com (192.168.111.1): icmp_req=6 ttl=64 time=0.109 ms
``````
           *-network
                description: Ethernet interface
                product: RTL8169 PCI Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: xx:xx:xx:xx:xx:xx
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.111.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yesport=MII speed=1Gbit/s
                resources: irq:18 ioport:cc00(size=256) memory:feafff00-feafffff memory:feac0000-feadffff
``````
doug@s10:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Half 1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes
```

---

### Post by tgalati4 on 2015-05-28
Change cables and change ports on the router.  Try booting with a LiveUSB and check the ping times--this is to isolate a clean boot versus an installed service issue.

---

### Post by Yanir_Jibly on 2015-06-10
I'm having the exact same problem. Definitely not the NIC, as I've tried both realtek and Intel.
Both are PCI cards, so I suspect it has something to do with it.  Moreover, it seems that it boots fine, and later on gets this weird behavior.
You should also notice that while it works fine, /proc/interrupts shows progress for the eth in question, while in the 99ms state, /proc/interrupts is simply stuck for this eth card.
I'm guessing it reverts to some kind of polling, hence the high latency, I still can't figure out the solution, it's driving me nuts.

---

### Post by Yanir_Jibly on 2015-06-11
Update: I see in dmesg that indeed the IRQ is being discarded, thus reverting to polling... (message is "irq ??: nobody cared (try booting with the "irqpoll" option)")
I don't seem to get that message anymore when I add: "acpi=force" to /etc/default/grub. I'm not sure this is a solution, as it may just be a workaround (e.g. perhaps these interrupts are now much slower to handle?). Still testing.

---

### Post by Yanir_Jibly on 2015-06-11
Another update: I think I found the culprit, at least for me - [https://lkml.org/lkml/2012/1/31/167](https://lkml.org/lkml/2012/1/31/167)
I've got an ASUS mobo, and it seems that PCI is actually going through a PCI to PCIe bridge called [COLOR=#000000]ASM1083[/COLOR], which is the one causing issues.
For now, I'm gonna try switch PCI slots hoping that that has something to do with it.

---

### Post by Yanir_Jibly on 2015-06-12
Seems like that did the trick for me. I've switched PCI slots, and the problem seems to have been solved. Hope you get the same results.

---

