---
title: "Router / Firewall"
date: 2017-04-25
forum: Ubuntu/Debian BASED
---

### Post by linuxyogi on 2017-04-25
Hi,

I want to make my Raspberry Pi a wired router/firewall. No need for wireless. I have given order for [this]("http://www.amazon.in/fast-Ethernet-Network-Adapter-White/dp/B00JPEOFT4?_encoding=UTF8&deviceType=desktop&redirect=true&ref_=ya_st_dp_summary"). 
 
No need for DHCP. I will assign IP Address/DNS manually.

I use cable broadband using Ethernet cable. The WAN interface has static IP.

WAN INTERFACE
---------------------------

IP                           172.16.197.xxx
Subnet Mask           255.255.255.0
Default Gateway      172.16.197.1
DNS                        8.8.4.4, 8.8.8.8             


I want to assign 192.168.0.X to the LAN interface.

How do I configure Raspbian ?

Please reply.

---

### Post by 1clue on 2017-04-25
[https://raspberrypi.stackexchange.com/questions/7223/using-the-raspberry-pi-as-a-router](https://raspberrypi.stackexchange.com/questions/7223/using-the-raspberry-pi-as-a-router)

This  is the first satisfactory result from googling "raspberry pi ethernet  router" but there will be thousands of hits if this one doesn't fit your  scenario.

That said:

If you have a typical internet connection in the USA then a pi will not keep up. The pi is limited by a single I/O chip, which handles all disk/usb/ethernet traffic. The nic is 100mbps, and on my pi's I can't even saturate it when pushing /dev/zero through eth0. I get about 66mbps doing that on a B+.

By doing NAT and routing, you add cpu load to the scenario. I would be really surprised if you can get 20mbps total throughput (both ways) as a router. I have 65mbps down and 7mbps up on my contract, and it's frequently better than that.

Another thing you have to consider is that this assumes moving large blocks of data and that the router (your pi) is the only bottleneck. In truth most traffic is small payloads and lots of them. And latency of your system also plays a part.

I would strongly recommend getting something which has 2 or more built-in Intel ethernet ports and a separate disk and/or usb chipset, and is known to be able to easily saturate both nics. That gives you plenty of CPU to handle NAT and port forwarding and that sort of thing.  Personally I wouldn't use anything with less than gigabit NICs, maybe Intel i210 or i35x. Something that uses the igb driver.  The reason I say this is because these cards handle much of the networking tasks right on the card and don't bother the CPU. Other NICs might be able to get the throughput but they have more interrupts which means the CPU is too busy handling those to do whatever it needs to do.

[https://www.netgate.com/products/pfsense-appliances.html](https://www.netgate.com/products/pfsense-appliances.html) has some interesting systems.
[https://routerboard.com/products/group/17](https://routerboard.com/products/group/17) has some more interesting systems.

I use this but it might be overkill: [URL="http://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm"]http://www.supermicro.com/products/motherboard/Atom/X10/A1SRM-LN7F-2758.cfm

[/URL]

---

### Post by SeijiSensei on 2017-04-25
Considering that you can buy an [Ethernet router for under $20]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833156001"), I'm not sure I see much value in buying new hardware and using Ubuntu for this task unless it's for educational purposes.

---

### Post by linuxyogi on 2017-04-25
> **SeijiSensei said:**
> Considering that you can buy an [Ethernet router for under $20]("https://www.newegg.com/Product/Product.aspx?Item=N82E16833156001"), I'm not sure I see much value in buying new hardware and using Ubuntu for this task unless it's for educational purposes.

The problem with home routers is the fact that the manufacturer stops releasing firmware updates and that makes it insecure. There is no guarantee that the router will support open source firmwares.
I have a old PC. I have downloaded pfSense. Once that usb to ethernet reaches me I will install pfSense.

BTW, I was not planning to use Ubuntu for the Pi. Its raspbian.

---

### Post by 1clue on 2017-04-26
As well, SOHO routers are notoriously easy to hack. Considering that they're closed source and almost all of them are made in China automatically makes me suspicious.

This might be overkill too considering the OP wants to try with a RPI. [http://www.wiredzone.com/supermicro-components-motherboards-embedded-processor-a2sdi-2c-hln4f-10027379](http://www.wiredzone.com/supermicro-components-motherboards-embedded-processor-a2sdi-2c-hln4f-10027379)

This is a brand new chip, and supports vt-d which my c2758 won't. Still supports the same 64g ram.  I like the idea of this sort of board because you can have a VM or 2 on this sort of box, donate NICs to them and then put your router(s) on that.  This was my intended approach with my board but the chip won't support vt-d so I'm not guaranteed isolation of the outside port from the host.

This looks like the final cost would be about a third of what I spent.

---

### Post by SeijiSensei on 2017-04-26
> **1clue said:**
> As well, SOHO routers are notoriously easy to hack. Considering that they're closed source and almost all of them are made in China automatically makes me suspicious.
You can buy routers that support open-source firmware like Tomato or ddWRT if you're that paranoid.  I have an ASUS that I flashed with ddWRT; works fine.

---

### Post by 1clue on 2017-04-26
> **SeijiSensei said:**
> You can buy routers that support open-source firmware like Tomato or ddWRT if you're that paranoid.  I have an ASUS that I flashed with ddWRT; works fine.

I feel like I'm injecting too much talk about high-end equipment into a discussion about a pi, but I think the things I have to say may apply.

I did the dd-wrt thing for awhile. I used it on a linksys router. I don't know if the web interface is any better but when I tried it the web interface was terrible. The updates for my hardware were few and far between, and quite a bit of the functionality I wanted was broken even in the command line. Some kernel options were not enabled.  Dd-wrt is great for the features everyone wants, not so much for advanced functionality. It's fantastically better than what comes on the stock SOHO routers, though.

All that, and now my internet speed is pretty high now, I had anticipated gigabit availability in my area but it still hasn't come and I question whether it will in the foreseeable future. My current setup, as nearly as I can tell, can handle 2.5 gbps continuously with compression included, and has hardware support for encryption as well which if all in one stream could still handle routing and vpn tasks almost to 1gbps. The ISP backed out of the gigabit connections in my area but I'm ready when it comes.

FWIW I've explored all sorts of options:
[LIST=1]
[*]Use an old PC with multiple nics.
[LIST=1]
[*]This uses a lot of power and a lot of room.
[*]The cost of the power all my old hardware uses would pay for a really good router in just a couple years.
[/LIST]

[*]Buy a SOHO router and use non-free firmware.
[LIST=1]
[*]VLANs and complex firewall rules are only available in really expensive hardware.
[*]VPN endpoint performance (router to router) is essentially nonexistent.
[*]These products tend to have planned obsolescence built into the product.
[/LIST]

[*]Buy a small business appliance and use non-free firmware.
[LIST=1]
[*]They start out very basic and then tack on fees to unlock features.
[*]Planned obsolescence.
[*]Limited scenarios for layout.
[/LIST]

[*]Buy a SOHO router and use dd-wrt or similar.
[LIST=1]
[*]The hardware is often substandard.
[*]VPN endpoint performance is essentially nonexistent.
[*]Many of the available systems can't handle the bandwidth I have, let alone what I hope to have soon.
[/LIST]

[*]Buy a small business appliance and use Linux.
[LIST=1]
[*]I don't have enough data on this. I'm afraid of proprietary hardware with no Linux drivers.
[/LIST]

[*]Buy a networking-specific board with good hardware.
[LIST=1]
[*]Every aspect of this is fantastic except the price.
[*]This is the route I took and will probably take again.
[*]What I got is fantastically faster than any connection I could hope to get.
[/LIST]
[/LIST]

---

### Post by linuxyogi on 2017-04-27
Just finished setting up pfSense. No more worries.

---

### Post by 1clue on 2017-04-27
What hardware did you use?

---

### Post by linuxyogi on 2017-04-27
AMD 64X2 5600+
Ram : 4GB
160GB HDD

---

