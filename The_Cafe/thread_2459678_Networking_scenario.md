---
title: "Networking scenario"
date: 2021-03-23
forum: The Cafe
---

### Post by MoebusNet on 2021-03-23
I've read several times that if several devices are connected to an Access Point, the slowest client's connection speed will slow the rest of the clients down, It got me to wondering: what is a greater cause of network congestion - devices connected at a lower speed than maximum-possible (e.g. 1000Mb vs 100Mb ethernet) or the possible additional data load from all devices connected at the highest speed possible (e.g. all 1000Mb ethernet.) Am I making any sense? An example would be a publicly-accessible network with random clients with random maximum-possible connection speeds. Which case would tend to limit network throughput more?

---

### Post by TheFu on 2021-03-23
> **MoebusNet said:**
> I've read several times that if several devices are connected to an Access Point, the slowest client's connection speed will slow the rest of the clients down, It got me to wondering: what is a greater cause of network congestion - devices connected at a lower speed than maximum-possible (e.g. 1000Mb vs 100Mb ethernet) or the possible additional data load from all devices connected at the highest speed possible (e.g. all 1000Mb ethernet.) Am I making any sense? An example would be a publicly-accessible network with random clients with random maximum-possible connection speeds. Which case would tend to limit network throughput more?

If by "Access Point", you mean "WiFi Access Point", which is called a WAP, then know that newer wifi protocols have tried to address the slow device problem since the AC protocol became standard.  Under N, G, B, and A, it was true that slower devices had a greater impact.

For wired connections, as 100base-tx or faster, the ethernet protocol deals with slicing each packet as available, so it isn't an important consideration.

Every switch or router has a maximum throughput inside the switch/router which is related to the "backplane" capacity.  Even cheap switches these days have plenty of backplane to support all the switch ports at maximum speed, but in them olden days, that wasn't the situation.  You might have a 24 port GigE switch that only had an 8Gbps backplane capacity, so only 8 Gbps of data could go through that switch at any point in time - not the 24Gbps all the switches would like.  And really, the PPS - packets per second are what networking gear specs are built on ... so here's a cheap, unmanaged, tp-link 8-port switch: [https://www.tp-link.com/us/home-networking/8-port-switch/tl-sg108/#specifications](https://www.tp-link.com/us/home-networking/8-port-switch/tl-sg108/#specifications)

That's 8 ports, each with 1 Gbps, right?  If we look deeper, we see Packet Forwarding Rate 	11.9Mpps in the specs. THAT will be the true limit almost always for throughput.  12 mega-pps.  
We also see Jumbo Frame 	16KB support. Historically, jumbo frames were 9k, not 16. Every jumbo frame device connected to this switch would need to be manually configured to 16Kb to make use of those larger packet sizes. It has been awhile, but I think the default size for ethernet packets is 1500b - 1.5K.  These settings are not auto-negotiated, which is too bad.  Also, when setting jumbo frame sizes on all our devices, problems are often caused by being off just 1 byte.  It was a common issue to set Jumbo frames to 9K, but the network device really only supported 9014b, not 9216b. 200b would be lost. That's bad.  
There are other limitations in the specs for that cheap switch - like a 4K MAC table, but I don't have anywhere near 4K devices in my LAN, so that isn't really any issue.  But inside an enterprise, it would be very bad.  OTOH, that's a $20 switch, so it won't be used in any enterprise.

Anyways, we've hit the limit of my knowledge at this point. Perhaps someone with actual network training will jump in?

---

