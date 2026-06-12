---
title: "PowerEdge 2900 - Ubuntu Server - PCIe Wireless Adapter Inquiry"
date: 2019-07-14
forum: Server Platforms
---

### Post by ethancahill on 2019-07-14
So I have recently setup Ubuntu Server on an old PowerEdge 2900, and was setting Ubuntu server up when it asked to connect to a network. Unfortunately the server does not come with any wireless wifi chip in it and this I can’t connect to the Network. I was wondering if I could buy and install would it work??: 

[https://www.officeworks.com.au/shop/officeworks/p/tp-link-300mbps-wireless-n-pci-express-adaptor-tptlwn881#features](https://www.officeworks.com.au/shop/officeworks/p/tp-link-300mbps-wireless-n-pci-express-adaptor-tptlwn881#features)

I do know I will have to download the drivers online but I just wanted to ask to see if this wireless adapter would work in an old PowerEdge 2900 server with Ubuntu server on it.

---

### Post by howefield on 2019-07-14
Thread moved to the "*Server Platforms*" forum.

---

### Post by SeijiSensei on 2019-07-15
Servers are designed to be hard-wired using Ethernet. They rarely come with a wifi card. The 2900 has [two Ethernet ports to the right of the USB ports on the back]("https://downloads.dell.com/manuals/all-products/esuprt_ser_stor_net/esuprt_poweredge/poweredge-2900_setup%20guide_en-us.pdf").

Put the server next to your router and connect one of the ports to the LAN side of your router with an Ethernet cable.

If you don't have one, [Amazon]("https://www.amazon.com/AmazonBasics-RJ45-Cat-6-Ethernet-Patch-Cable-5-Feet-1-5-Meters/dp/B00N2VILDM") sells them for a little as $4. If you're in a hurry you can buy one at Best Buy, but they're way more expensive there.

---

