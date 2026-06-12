---
title: "problems installing new network interface - dhcp ok but no active connection"
date: 2009-05-16
forum: Server Platforms
---

### Post by gobbledigook on 2009-05-16
Hi, i am running ubuntu 9.04 as a file server at home, i recently got a gigabit router and soon realised that my servers onboard eth was not gigabit, d'oh!

so i have got a gigabit eth adapter, pci slot one and plugged it in, rebooted, and added it to my /etc/network/interfaces file as follows remembering to restart network after:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.120
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

#The secondary network interface (10/100/1000)
auto eth3
iface eth3 inet dhcp

```

now when i hot-swap the ethernet cable it does dhcp to my router, the MAC is assigned an ip in the dhcp table. However it does not appear in the 'active clients' list and i am not able to connect to it via ssh or samba nor does it respond to pings.

anyone have any ideas? below is some more info specific to the eth3 device:

```

sudo ethtool eth3
Settings for eth3:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no

```

thanks, 

Dan

---

### Post by spacesamurai on 2009-05-16
Looking at your output, there are two things that might be related.

1. Eth3 is running in half duplex. Is your router also set to half duplex as well? Nowadays most connections are done in full, so you might want to check both ends and make sure they are running the the same duplex.

2. You list Eth0 and then Eth3. These interfaces are usually listed logically, so the next interface after Eth0 should be Eth1. You could run the following command to see how the interfaces are configured.

```
lshw -c network
```

Hope this helps.

---

### Post by gobbledigook on 2009-05-16
hi there! and thanx for your reply:)

i think you are on to the issue with the duplexing part, however i am having trouble trying to configure the card to accept 1000tx full duplex, i have tried with:
```

sudo ethtool --change eth3 speed 1000 duplex full

```

this completes with no errors, however it seems to make no difference, i have tried with ifdown eth3, command, then ifup eth3, with both sudo and not with the same result,

also i have tried with:
```

 mii-tool -F 1000baseTx-FD eth3
invalid media specification '1000baseTx-FD'.

```

with the resulting error, this is the same with the if up/down and sudo.

the out put of lshw -c network is:
```

sudo lshw -c network
[sudo] password for server:
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth3
       version: 10
       serial: 00:21:27:c9:69:c4
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:90:f5:2d:f9
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.120 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

```

so if my device is ok, i think it may be a matter of telling eth3 to go to 1000tx full duplex, but as explained above i am having trouble executing this. 

just checked the box it arrived in and it states:

"data rate: 10/100Mbps for half duplex, 20/200/2000Mbps for full duplex"

hope this helps!

thanyou,

Dan

ps i don't have an ethernet plugged into this at the moment as the server is headless so i need the working eth connection to ssh into it:)

---

### Post by gobbledigook on 2009-05-17
hey! 

i worked it out:) the commands only work when there is an active link!

so i hooked up an extra cable and did commands:

```

sudo ifdown eth3
sudo ethtools --change eth3 speed 1000 duplex full
sudo ifup

```

and i'm all good to go! thnks to spacesamurai for helping me work that ome out, i knew it would be something simple that i didn't know about;)

dan

---

### Post by spacesamurai on 2009-05-17
I am glad to hear that your network is up and running (I wish I had that type of speed on my own). Nowadays you don`t see the half duplex too often, which kind of stuck out when I saw your output. It also seems that this time the properties of the interface could only be changed when it was first disabled. 

Happy networking ;)

---

