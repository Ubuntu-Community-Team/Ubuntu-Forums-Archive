---
title: "Why use a dedicated machine as a gateway?"
date: 2009-12-31
forum: Server Platforms
---

### Post by garfonzo on 2009-12-31
Hey folks,

Just curious, how many of you have a dedicated machine that all of your internet flows through? For example, this scenario:

Inter-tubes --> **Gateway/Routing Machine** --> Switch --> Server and all machines on the LAN

I have a bunch of old machines and was thinking of setting this up but I don't see any benefit since I have a Linksys router. What benefit is there of setting up a dedicated machine for routing?

Thanks,

Garfonzo

---

### Post by b0b138 on 2009-12-31
For your home, probably none as your linksys as acting as a gateway/router/switch.  Unless you wanted to just for the sake of doing it.

From a buisness side with say, 500 users, you got 500 computers going to 20 switched/hubs (assuming 25 on each) -> gateway/router/firewall ( cause you also have to worry about what goes out, ie. content filtering  ie. no youtube on the clock) and that sort of application might involve seperate machines. So might go 500 pcs -> hubs/routers -> gateway/content filtering/ web caching -> firewall -> net

---

### Post by BkkBonanza on 2009-12-31
It's mostly a question of capacity. If you have a Linksys and have flashed DD-WRT or one of the other upgrades then you have most of the features already. I have an upgraded Linksys and the main downfall is for LAN traffic as it just can't handle much bandwidth at all. Traffic through it seems to top out at about 4-5 Mbps. The nice thing about the Linksys is it doesn't use as much power as a dedicated machine.

---

### Post by CharlesA on 2009-12-31
> **BkkBonaza said:**
> It's mostly a question of capacity. If you have a Linksys and have flashed DD-WRT or one of the other upgrades then you have most of the features already. I have an upgraded Linksys and the main downfall is for LAN traffic as it just can't handle much bandwidth at all. Traffic through it seems to top out at about 4-5 Mbps. The nice thing about the Linksys is it doesn't use as much power as a dedicated machine.

This pretty much. I set up a spare box as a gateway/filter/web cache, but ended up taking it down since using a regular Linksys or Dlink was easier.

---

### Post by BkkBonanza on 2009-12-31
Regarding my note above - I have a switch on the inside of my Linksys which allows my LAN to operate at speeds higher than the router can handle. It seems even the very cheapest switches are faster than these routers. I don't know what a Gigabit switch costs but having one would mostly offset any problems with the Linksys speed limit.

edit: apparently $20 on ebay for a netgear one. Anyone have a recommendation for a gigabit switch model they've tested to it's rated speed?

---

### Post by ratcheer on 2009-12-31
I am using two Netgear gigabit switches for the past few years and they hve been rock solid. I started with a 4-port that cost me $50, but my devices exceeded the number of ports so I replaced it with an 8-port model about a year ago. I think I paid about $80 for it.

I don't know whether they meet their speed ratings, but they are plenty fast for my home LAN. My DSL service is only 3 mbps and they far exceed that.

My network topography is that the DSL modem acts as the gateway, router, and DHCP server. It is plugged into the Netgear switch. Then, two PC's are plugged directly into the switch. A third PC, in a somewhat distant room, is connected via two Netgear power line adapters, one of which is plugged into the switch. Finally, there is a Netgear WNDR3300 wireless N dual band router which is configured as a wireless access point, also plugged into the switch. It provides connectivity to a Macbook Pro, a PS3, a PSP, and an iPod Touch. It all works, all the time.

Tim

---

### Post by CharlesA on 2009-12-31
> **BkkBonaza said:**
> Regarding my note above - I have a switch on the inside of my Linksys which allows my LAN to operate at speeds higher than the router can handle. It seems even the very cheapest switches are faster than these routers. I don't know what a Gigabit switch costs but having one would mostly offset any problems with the Linksys speed limit.

edit: apparently $20 on ebay for a netgear one. Anyone have a recommendation for a gigabit switch model they've tested to it's rated speed?

That's what I've done. Running my LAN machines thru a Gigabit switch and hooking up the switch to the router.

The two I've been using are these here:

[D-Link 8-port Gigabit switch]("http://www.amazon.com/gp/product/B000FITKK8")
[D-Link 5-port Gigabit switch]("http://www.amazon.com/gp/product/B000FIVDIA")

So far I've been able to hit read/write speeds of up to 100MB/sec

> **ratcheer said:**
> My network topography is that the DSL modem acts as the gateway, router, and DHCP server. It is plugged into the Netgear switch. Then, two PC's are plugged directly into the switch. A third PC, in a somewhat distant room, is connected via two Netgear power line adapters, one of which is plugged into the switch. Finally, there is a Netgear WNDR3300 wireless N dual band router which is configured as a wireless access point, also plugged into the switch. It provides connectivity to a Macbook Pro, a PS3, a PSP, and an iPod Touch. It all works, all the time.

Tim

Mine is similar. Router --- 8-port switch --- 5-port switch

I've got some PCs hooked up to the 8 port and some to the 5 port. All are connected with CAT5e. Some devices, My VoIP phone for instance, run at 10/100, router is 10/100, printer is wireless, don't seem to have any affect on bringing the switch down to 10/100.

Also as a sidenote: I converted to Gigabit Ethernet probably 6 months ago, and never looked back. I'm not even using Jumbo Frames (MTU > 1500).

---

