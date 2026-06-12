---
title: "link aggregation device to work from the box"
date: 2018-08-01
forum: The Cafe
---

### Post by marchello_lippi2 on 2018-08-01
Hi all, 
I would like to buy some device for **link aggregation** (this technology has also other names like **port trunking, ****link bundling, ****Ethernet/network/NIC bonding, ****NIC teaming**) that will work from the box. 

The goal is [FONT=sans-serif]combining ([/FONT]*[aggregating]("https://en.wiktionary.org/wiki/aggregation")) multiple network connections in parallel in order to increase [throughput]("https://en.wikipedia.org/wiki/Throughput") beyond what a single connection could sustain, and to provide [redundancy]("https://en.wikipedia.org/wiki/Redundancy_(engineering)") in case one of the links should fail.*

The idea is described in the wiki: [https://en.wikipedia.org/wiki/Link_aggregation](https://en.wikipedia.org/wiki/Link_aggregation)

As a private person, I would rather have something not too expensive. 

Any advise appreciated. Thx ahead.

---

### Post by TheFu on 2018-08-03
You need network devices which support it along with network cards for the computer. There is a specific 802.something protocol which provides this support. That is what you need.  A cheap switch with this support is $75-$150.  Any intel PRO/1000 NIC can do it. Those are $25/ea.  If you buy a dual port card, it should work, but the PCI bus port might not support the throughput. You'll need to research the backplane on your intended motherboard.  Server motherboards usually have multiple internal buses, so you can place different NICs onto each bus and further enhance redundancy.

Redundancy in NICs really doesn't pay.  In 25 yrs, I've only seen 2 NICs fail on any of my home or work projects. That's more than 500 servers. NICs just don't fail that often.

I hear that 10G networking is getting cheap enough for home users.  Last time I looked was a few years ago when my ISP offered 2Gbps connections in advertising. It was outside my price.

---

### Post by marchello_lippi2 on 2018-08-05
Ok, I believe dual port card should do the trick. 
However I would like to have some switch that will work out of the box. Like putting N uplink ethernet cables into device and switching "link aggregation" button **on** in its gui interface. All the rest devices behind that router should use this aggregated traffic without any additional settings. Have you or someone else heard of anything like this? 

If not, well, shoot happens, I will try to use intended home server for this.. Though this will be prio number [last number in my current list +1] ..

---

