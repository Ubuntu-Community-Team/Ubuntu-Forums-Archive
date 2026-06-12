---
title: "Using ubuntu server as NAT gateway, throughput slower than cheap router!"
date: 2010-11-26
forum: Server Platforms
---

### Post by Csutcliff on 2010-11-26
Hi, I've been using an Ubuntu 10.04.1 server as a general (samba, squid, UPnP-igd, OpenVPN) server for my LAN which is working well now.

I Also use it as the firewall/NAT router for my internet connection (PPPoE on 2nd ethernet port), this also works well but with one caveat, which is it is outperformed by a cheap consumer grade router!

With such a router the WAN -> LAN troughput is almost equal to the sync speed of the ADSL2+ modem (usually around 15Mbps) however when using my ubuntu server as gateway the throughput is only around 900Kbps and I'm at a loss as to what might be causing this.

So far i've tried with all other services disabled (although CPU and RAM usage are always very low)

Downloading straight from the server yeilds an improved rate but even then it isnt a match for a cheap router.

Does anyone have any ideas?

Thanks

---

### Post by elico on 2010-11-26
it looks kind of simple Ethernet Speed settings thing.

im using ubuuntu server as NAT\gateway mail server and much more on an ATOM based system and it works on GB speed :) so it's not the server OS.

also there are many production servers firewalls gateway and much more so..
i assume you are getting me.

so you have ADSL modem connected to one of the ETH ports of the server so i assume your interfaces are something like eth0 eth1 and pppo.

that most likely will give you the answer to the source of the problem.
if your eth0 is connected to the ADSL modem check the interface speed with:

```
ethtool eth0
output:
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes


```

or

```
mii-tool
output:
eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok

```

commands

---

### Post by Csutcliff on 2010-12-19
Sorry for the late reply, Alas it doesn't seem to be that simple, the Ethernet port which the modem is connected to is running at 100mbps full duplex.

---

