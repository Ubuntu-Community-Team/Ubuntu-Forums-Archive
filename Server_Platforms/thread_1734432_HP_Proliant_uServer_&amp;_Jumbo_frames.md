---
title: "HP Proliant uServer &amp; Jumbo frames"
date: 2011-04-20
forum: Server Platforms
---

### Post by schander on 2011-04-20
Hi all,
I have one of these [HP MicroServers]("http://h10010.www1.hp.com/wwpc/uk/en/sm/WF05a/15351-15351-4237916-4237917-4237917-4248009.html") I'm currently running ubuntu server 10,10 64bit on it with 5gb ram.
If I look at the hardware spec using lshw I find that it contains the following:
```

*-network
    description: Ethernet interface
    product: NetXtreme BCM5723 Gigabit Ethernet PCIe
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 10
    serial: 68:b5:99:72:ce:c3
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5723-v3.35 ip=192.168.0.205 latency=0 multicast=yes
    resources: irq:42 memory:fe9f0000-fe9fffff
```
Whenever I try and enable Jumbo frames, anything over 1500 I get the following error:
SIOCSIFMTU: Invalid argument
Broadcom have released a newer version of the driver, 3.116j (dated 22/03/2011). Have had a quick look at there [programmers guide]("http://www.broadcom.com/collateral/pg/5723-PG100-R.pdf") It looks as though it should support jumbo frames.

[LIST]
[*]Has anyone managed to get jumbo frames with NIC/class of nic?
[*]Would it be worthwhile exercise compiling/installing the new driver?
[*]Have I missed something obvious?
[/LIST]

Thanks
Satpal

---

### Post by usatonycuba on 2011-04-20
> **schander said:**
> Hi all,
I have one of these [HP MicroServers]("http://h10010.www1.hp.com/wwpc/uk/en/sm/WF05a/15351-15351-4237916-4237917-4237917-4248009.html") I'm currently running ubuntu server 10,10 64bit on it with 5gb ram.
If I look at the hardware spec using lshw I find that it contains the following:
```

*-network
    description: Ethernet interface
    product: NetXtreme BCM5723 Gigabit Ethernet PCIe
    vendor: Broadcom Corporation
    physical id: 0
    bus info: pci@0000:02:00.0
    logical name: eth0
    version: 10
    serial: 68:b5:99:72:ce:c3
    width: 64 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=tg3 driverversion=3.110 firmware=5723-v3.35 ip=192.168.0.205 latency=0 multicast=yes
    resources: irq:42 memory:fe9f0000-fe9fffff
```
Whenever I try and enable Jumbo frames, anything over 1500 I get the following error:
SIOCSIFMTU: Invalid argument
Broadcom have released a newer version of the driver, 3.116j (dated 22/03/2011). Have had a quick look at there [programmers guide]("http://www.broadcom.com/collateral/pg/5723-PG100-R.pdf") It looks as though it should support jumbo frames.

[LIST]
[*]Has anyone managed to get jumbo frames with NIC/class of nic?
[*]Would it be worthwhile exercise compiling/installing the new driver?
[*]Have I missed something obvious?
[/LIST]

Thanks
Satpal
It looks as though it should support jumbo frames, (your switch/router does? ). but.. maybe not at that specific state.. why not try a lower value.. 9k jumbo ? :
```
sudo ifconfig eth0 mtu 9000
```

---

### Post by schander on 2011-04-21
> **usatonycuba said:**
> It looks as though it should support jumbo frames, (your switch/router does? ). but.. maybe not at that specific state.. why not try a lower value.. 9k jumbo ? :
```
sudo ifconfig eth0 mtu 9000
```
Thanks for your reply.
I have tried frame sizes 1600/1700/1800/2k/3k/4k/5k/7k/9k
Actually I hadn't thought about my switch not handling jumbo frmaes. It's a [Netgear GS 105]("http://www.netgear.co.uk/business/products/switches/unmanaged-desktop-switches/GS105.aspx") I have just found [this]("http://kb.netgear.com/app/answers/detail/a_id/222/~/what-is-the-jumbo-frame-supported-by-switches-and-adapters%3F") and my switch has a serial number begining with 1FD. I think I might raise a question on the Netgear forums.
Also I might try the setup with just the Nas and my pc (which does have jumbo frame support, just in case the switch defaults to the lowest common denominator as I have the switch also connected to a Devolo 200mpbs home plug. 

Thanks Again
Satpal

---

### Post by amp06 on 2011-04-21
According to Broadcom's Programmer's Guide for the BCM5723 NIC chipset, the hardware does NOT support jumbo frames.

[http://www.broadcom.com/products/Ethernet-Controllers/Enterprise-Server/BCM5723](http://www.broadcom.com/products/Ethernet-Controllers/Enterprise-Server/BCM5723)

The table on page 4 of the .pdf reads "Jumbo Frame Support      No"

I have an HP Microserver and am a little disappointed that they went with this NIC if this information is still current. I just bought the server though, and haven't even finished setting it up... so it's too early for me to judge performance. If it looks like jumbo frames will help, I guess I could just add an Intel PCIe NIC.

---

### Post by schander on 2011-04-26
> **amp06 said:**
> According to Broadcom's Programmer's Guide for the BCM5723 NIC chipset, the hardware does NOT support jumbo frames.

[http://www.broadcom.com/products/Ethernet-Controllers/Enterprise-Server/BCM5723](http://www.broadcom.com/products/Ethernet-Controllers/Enterprise-Server/BCM5723)

The table on page 4 of the .pdf reads "Jumbo Frame Support      No"

I have an HP Microserver and am a little disappointed that they went with this NIC if this information is still current. I just bought the server though, and haven't even finished setting it up... so it's too early for me to judge performance. If it looks like jumbo frames will help, I guess I could just add an Intel PCIe NIC.

That is just pants.... I missed that when looking at the pdf, i went straight for the technical info..
Looking at the code supplied in the latest tg3 driver I looked to me as though the Jumbo frame support was related to the Kernel supporting them, i could have got that wrong through :(

Regards
Satpal

---

