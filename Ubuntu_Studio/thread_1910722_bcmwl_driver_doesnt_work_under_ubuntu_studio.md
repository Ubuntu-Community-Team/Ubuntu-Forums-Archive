---
title: "bcmwl driver doesnt work under ubuntu studio"
date: 2012-01-17
forum: Ubuntu Studio
---

### Post by beefbonanza on 2012-01-17
hi everybody,
I recently installed the realtime kernel and Ubuntu Studio packages. Now, my WiFi-module (Broadcom BCM4312 on a Dell Vostro 1310) doesn't work no more. I was using the proprietary Broadcom WL Driver before, when I'm now trying to re-activate it (additional drivers menu, driver listed NOT activated) it fails, logging the following to /var/log/jockey.log:
```

2012-01-17 22:26:37,823 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-01-17 22:26:37,930 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```any ideas how i can get the card working?

---

