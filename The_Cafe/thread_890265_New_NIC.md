---
title: "New NIC"
date: 2008-08-14
forum: The Cafe
---

### Post by Dr Small on 2008-08-14
The internal ethernet adapter on my 7-8 year old motherboard is going bad and I need to replace it (this is for my server). Does anyone have any recommendations of a NIC that would work with Ubuntu?

According to lshw, this is my current ethernet:
```
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:10:dc:99:a3:41
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.0.70 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: ioport:e000-e0ff iomemory:dffffe00-dffffeff irq:17

```

Dr Small

---

