---
title: "Q:  Default routing"
date: 2010-11-30
forum: Security
---

### Post by Trandre on 2010-11-30
I have installed Ubuntu on my work laptop computer as a dual boot option. 

Although having local administrator account the Company's it responsible has set up a monitoring configuration that is too extensive for my taste. All network traffic is routed through the companies server and the traffic is stored. 

My Question is will the Ubuntu install be affected by this routing policy or will that be only applicable for the XP install? 

Is there a way that I can check if this setting is on in the Ubuntu install?

---

### Post by endotherm on 2010-11-30
well routing is all part of the TCP/IP stacks job, and since all IP stacks are built to be compatible, there should be no problem handling the routing. the application of the settings however is likely tricky. unless some one came down and configured your route, you are using the gateway pushed down by your dhcp server, and the default gateway is derived from the local gateway information. 


to view your routes, just open a terminal and enter:
```
route
```

---

### Post by SeijiSensei on 2010-11-30
> **Trandre said:**
> Although having local administrator account the Company's it responsible has set up a monitoring configuration that is too extensive for my taste. All network traffic is routed through the companies server and the traffic is stored.

They must have some really large disks.  All the traffic is stored? Or, is it really just logged?

If you mean that the company tracks your HTTP requests, then if they're using a transparent proxy like Squid, you're unlikely to get past that easily.  There are some other methods, but I'm not going to mention them here.  In addition, if they enforce the same security policies my clients do, those methods wouldn't work either.

---

