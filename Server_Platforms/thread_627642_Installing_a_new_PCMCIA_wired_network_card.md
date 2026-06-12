---
title: "Installing a new PCMCIA wired network card"
date: 2007-11-30
forum: Server Platforms
---

### Post by 505 on 2007-11-30
Hi,

I have an old laptop set up as a server, and it's running headless. Because the laptops network port is failing (cable not staying in) I bought a PCMCIA wired network card. It's a SMC8040TX. When I insert it, on the card the TX light goes on, and on screen I get
```

pccard: PCMCIA card inserted into slot 1
pcmcia: registering new device pcmcia1.0
eth1: NE2000 (DL10022 rev 05): io 0x300, irq 3, hw_addr 00:E0:98:90:E5:C0

```
BUt after that I have no idea what to do. When I attach the cable to this new card nothing happens (no extra lights), and when  type 'ifup eth1' I get
```

Ignoring unknown interface eth1=eth1.

```
You should I configure this new card. I want to use it as the primary network interface. I don't need dynamic configuration (e.g. that card will not be unplugged) and the IP address should be static.

Thanks for you help.
Daniel

---

