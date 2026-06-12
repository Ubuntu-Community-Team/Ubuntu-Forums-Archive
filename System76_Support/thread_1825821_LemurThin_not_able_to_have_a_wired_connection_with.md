---
title: "LemurThin not able to have a wired connection with Network Switch"
date: 2011-08-15
forum: System76 Support
---

### Post by TapocoL on 2011-08-15
I have a LemurThin laptop. I have started wiring my house and want all rooms to connect to a single switch (which connects to my router). I have not had wired connection problems before with the router (only wireless problems).

Now, I am trying to connect to the switch, however all I see in the taskbar is "Wired Network disconnected". The switch is not even showing a flickering of light for the port connected. When I use the same cable plugged into the same port of my switch with my Mac, it connects fine. When, I use the same cable and connect directly to the router with both laptops, they both work fine.

So, the only problem I seem to be running into is, that my LemurThin and my switch are not able to communicate.

Here are some details:
system76 model: lemu1
Trendnet switch model: TEG-S80g
system76 driver version: 2.6.8

Let me know if you need more details about my system.

Thanks,
Craig

---

### Post by Furball588 on 2011-08-16
Things I might try...

Disconnecting all devices connected to the switch except for the Lemur.

Try a different port.  

Are you seeing comparable results with the ethernet LEDs at the laptop?

Apparently the speed won't light at the switch if it links at 10 Base T.  

I'm thinking there's something conflicting with it on the network, be it a MAC address, an IP address or something else.

---

### Post by isantop on 2011-08-18
I have to concur with the above post; trying it with the Lemur as the only thing connected to the switch would be the best test right now.

---

### Post by TapocoL on 2011-08-18
Not much luck with that. Still wasn't detecting a link on eth0.

Here are some commands with response if any will help:

```
$ dmesg | grep -i eth0
[    2.426311] jme 0000:06:00.5: eth0: JMC250 Gigabit Ethernet ver:23 rev:3 macaddr:00:90:f5:96:d0:4d
[   18.734880] jme 0000:06:00.5: eth0: Link is down
[   18.735714] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
$ lspci | grep -i ether
06:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
```

```
$ ethtool -i eth0
driver: jme
version: 1.0.7
firmware-version: 
bus-info: 0000:06:00.5
```

```
ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: g
        Current message level: 0x000020c6 (8390)
                               probe link rx_err tx_err hw
        Link detected: no
```

```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:90:f5:96:d0:4d  
          inet6 addr: fe80::290:f5ff:fe96:d04d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5916421 (5.9 MB)  TX bytes:839487 (839.4 KB)
          Interrupt:47
```

---

### Post by Furball588 on 2011-08-18
Am I reading this right?  It linked at 10BaseT Half duplex?

I guess is there a way to disable the auto-negotiate and then maybe look at the kernel log?

---

### Post by isantop on 2011-08-19
I've been doing some research on this, and I've come across some interesting findings.

We also have a TEG-S80g here in the office, and no matter how hard I tried, I couldn't get our test Lemur to connect to it either, while seemingly every other system we had. 

So I looked at the Ethernet card in the Lemur (a JMicron JMC250). Another computer we have with that chipset is the Pangolin PanP7, and when I tried one of those on the switch, it also failed to connect every time. It isn't just in the BIOS either; I can't netboot with these machines and this switch either. And when I googled this combination, the limited results I found pointed to further incompatibilities between this NIC and this switch.

It looks like this is a hardware incompatibility. Would it be possible to use a different switch?

---

### Post by Flyers2391 on 2011-08-19
I've seen auto-negotiation go to 10 / half if one side was hard set.  I just looked up that switch and see it is unmanaged so that side doesn't look like a possibility unless it is bad firmware or something.  Have you tried to hard-set the lemur port to 100 / full (or gig/full even though that is against spec)?  

I actually don't know how to hard set the port in the GUI (I would think it would be simple but I don't see the option at the moment) so you may have to drop into the terminal.

---

