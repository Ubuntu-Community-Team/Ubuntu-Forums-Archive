---
title: "WiFi tethering for net sharing"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by calanor on 2012-02-21
Hi,

I was pretty pleased with Ubuntu 12.04 when finally just clicking "Use as Hotspot" started an ad-hoc WiFi network from my laptop and others were able to share my Internet connection. However I also came to know that my android phone doesn't see ad-hoc networks. Does anyone know how to make a non ad-hoc WiFi network in ubuntu ?

---

### Post by portis on 2012-02-21
You can google hostapd.
Your wifi card must support master mode.

> **calanor said:**
> Hi,

I was pretty pleased with Ubuntu 12.04 when finally just clicking "Use as Hotspot" started an ad-hoc WiFi network from my laptop and others were able to share my Internet connection. However I also came to know that my android phone doesn't see ad-hoc networks. Does anyone know how to make a non ad-hoc WiFi network in ubuntu ?

---

### Post by Gregory Lee on 2012-02-21
I suppose you mean with just a mouse click?  Dunno.  I just set up one of these: "Wireless 802.11N Router w/ WPS & WISP Function (150Mbps), #8071, $19.20", from Monoprice.com.  I used it to connect by ethernet cable to my old access point (wireless router) and provide an additional access point.  It provides a nice strong signal.  I really wanted to extend the range of my old wireless network, but so far as I can tell, this part only makes a new network, if connected as I have it.

---

### Post by JRV on 2012-02-21
> **calanor said:**
> Hi,

I was pretty pleased with Ubuntu 12.04 when finally just clicking "Use as Hotspot" started an ad-hoc WiFi network from my laptop and others were able to share my Internet connection. However I also came to know that my android phone doesn't see ad-hoc networks. Does anyone know how to make a non ad-hoc WiFi network in ubuntu ?

Where is this "Use as Hotspot" option?
I can't find it anywhere.

---

### Post by Gregory Lee on 2012-02-21
> **JRV said:**
> Where is this "Use as Hotspot" option?
I can't find it anywhere.
System Settings > Network > Wireless > Use as Hotspot

---

### Post by JRV on 2012-02-21
> **Gregory Lee said:**
> System Settings > Network > Wireless > Use as Hotspot

Thank you, I will have to investigate that.

---

### Post by hugmenot on 2012-02-21
> **portis said:**
> You can google hostapd.
Your wifi card must support master mode.

Short, sweet, /and/ correct. Surprised there are still knowledgable people around.

---

### Post by calanor on 2012-02-21
Thanks, I will look into it and report back.

---

