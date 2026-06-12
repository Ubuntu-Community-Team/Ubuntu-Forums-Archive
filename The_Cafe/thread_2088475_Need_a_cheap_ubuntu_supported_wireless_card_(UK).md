---
title: "Need a cheap ubuntu supported wireless card? (UK)"
date: 2012-11-26
forum: The Cafe
---

### Post by ELD on 2012-11-26
Okay so currently my pc is connected to the net via a powerline adapter which is giving me a bad connection.

I am looking for a decent but cheap PCI wireless adapter that works out of the box in Ubuntu 12.10.

I am in the UK so no american sites please.

---

### Post by coffeecat on 2012-11-26
> **ELD said:**
> Okay so currently my pc is connected to the net via a powerline adapter which is giving me a bad connection.

Sorry to hear that. I find that powerline is more dependable than wireless.

> **ELD said:**
> I am looking for a decent but cheap PCI wireless adapter that works out of the box in Ubuntu 12.10.

Not PCI, but I can recommend two USB wireless adaptors that "just work" with Ubuntu 12.04 and 12.10...

> **ELD said:**
> I am in the UK so no american sites please.

Indeed! These are the two and I am very pleased with them both:

[http://www.amazon.co.uk/TP-Link-TL-WN822N-300MBPS-Wireless-Adapter/dp/B003VIY03Q/ref=sr_1_1?ie=UTF8&qid=1353962343&sr=8-1](http://www.amazon.co.uk/TP-Link-TL-WN822N-300MBPS-Wireless-Adapter/dp/B003VIY03Q/ref=sr_1_1?ie=UTF8&qid=1353962343&sr=8-1)

[http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1](http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1)

One caveat - some wireless device manufacturers have been known to change the wireless chipset in the device but keep the same model number. All I can say is that the ones I have work just fine. I'm posting courtesy of the 300Mbps one and lsusb gives me:

```
Bus 001 Device 002: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N v3 802.11n [Atheros AR7010+AR9287]

```

Something to think about. I've given up with PCI adapters. Their placing means that they are often partly shielded from the wireless signal. USB adapters might mean that you have a cable trailing around but at least you have some flexibility in where you place them.

---

### Post by ELD on 2012-11-26
Well for some reason my powerlines gives about 8mb/s on speed test sites, my fiances mac on wireless gives her between 20-30mb/s so i'm getting really bad connection.

Probably the houses wiring!

Do you get a decent speed with your USB ones? I've been told USB adapters give you a much slower speed as USB is a lot slower than PCI.

---

### Post by LuciferRex on 2012-11-26
> **ELD said:**
> Do you get a decent speed with your USB ones? I've been told USB adapters give you a much slower speed as USB is a lot slower than PCI.

For a while, I had no choice but to use USB WiFi.  In my experiences, the internet service limited my connectivity FAR more than the USB adapter.

---

### Post by coffeecat on 2012-11-26
> **ELD said:**
> 
Do you get a decent speed with your USB ones? I've been told USB adapters give you a much slower speed as USB is a lot slower than PCI.

About 6.9 Mbps download whether I use wireless or ethernet. I've not really understood the argument that USB slows down internet speeds. According to this wikipedia article:

[http://en.wikipedia.org/wiki/Universal_Serial_Bus](http://en.wikipedia.org/wiki/Universal_Serial_Bus)

You should expect about 280 Mbps with USB2 which is way above what most people can get from broadband. USB1 probably slowed things down and perhaps that idea has simply stuck like an urban myth.

---

### Post by Mmmbopdowedop on 2012-11-26
> A USB connection has a maximum speed of 480Mbps

A PCI card is a hell of a lot times faster at transferring/processing data, but your connection is only giving your 30Mbps on a good connection, you say, thus, the difference is negligible.

If a USB one is guaranteed to work and is cheaper. Buy it.

*Coffeecat just beat me there. ;)

---

### Post by ELD on 2012-11-26
Well i went for this one
[http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1](http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1)

Since it has free delivery too :D

---

### Post by coffeecat on 2012-11-26
> **ELD said:**
> Well i went for this one
[http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1](http://www.amazon.co.uk/TP-Link-TL-WN722NC-150Mbps-Wireless-Adapter/dp/B003158RHE/ref=sr_1_1?ie=UTF8&qid=1353962418&sr=8-1)

Since it has free delivery too :D

Good luck!

If you look through the customer reviews for that item you'll see that some are using it with Ubuntu. :)

---

### Post by lz1dsb on 2012-11-26
I use D-link DWA-131 USB Wireless adapter. It's fully supported in the Linux Kernel. It's relatively cheap. But I haven't really tested it for speed...

---

### Post by ELD on 2012-11-26
> **coffeecat said:**
> Good luck!

If you look through the customer reviews for that item you'll see that some are using it with Ubuntu. :)

Ideal i shouldn't be sorry then!

Just got to scrape money together over the next month to get an nvidia graphics card and I am all set!

---

### Post by Primefalcon on 2012-11-26
We just got a couple of pci-e cards, I actually asked for advice on these forums for advice myself... let me check If I can fin the post:

[http://ubuntuforums.org/showthread.php?t=2078424](http://ubuntuforums.org/showthread.php?t=2078424)

and I have them in 11.10, 12.04 and 12.10 machines and they run perfectly out of the box

---

### Post by tartalo on 2012-11-27
My recommendation is any PCI card with an Atheros chipset, they tend to be cheap and thanks to the free driver they work perfectly out of the box in every Linux distribution I have tried.

Edit: Oh, apparently I was just lucky and not EVERY atheros chipset works out of the box: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by mythic97 on 2012-11-27
i use a TP LINK 300mbs dongle that works a treat
and these guys make the best

---

### Post by HansKisaragi on 2012-11-27
cnet cwp-854, best wifi card ever

been using the same card in my last 2 pcs

[IMG]http://www.needbuying.com/shopping/images/aablms/CNET-WP854.jpg[/IMG]

---

### Post by szymon_g on 2012-11-27
get anything from intel- their wi-fi cards are well supported under linux, their desktop versions are based on the same chipsets as their mobile ones.

---

### Post by sdowney717 on 2012-11-27
I bought one for a dollar off ebay
It is a tiny USB thing sold by TomTop

802.11N
this is the same one.

[http://www.ebay.com/itm/Mini-USB-150Mbps-WiFi-Wireless-Adapter-150M-Network-LAN-Card-802-11n-g-b-/261134495121?pt=LH_DefaultDomain_0&hash=item3cccd42d91](http://www.ebay.com/itm/Mini-USB-150Mbps-WiFi-Wireless-Adapter-150M-Network-LAN-Card-802-11n-g-b-/261134495121?pt=LH_DefaultDomain_0&hash=item3cccd42d91)

> Bus 002 Device 007: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter


---

