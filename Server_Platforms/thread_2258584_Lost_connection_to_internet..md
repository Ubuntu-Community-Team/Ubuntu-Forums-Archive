---
title: "Lost connection to internet."
date: 2014-12-28
forum: Server Platforms
---

### Post by brownd7380 on 2014-12-28
So I have Ubuntu server 14.04 as my home server. I can ping other devices on my home network but get nothing from pinging google. I also can ping 8.8.8.8 no problem, not sure if that helps. I am a noob and need some help.

Thanks,

Dustin.

---

### Post by steeldriver on 2014-12-28
It sounds like a problem with your DNS configuration - can you post the contents of your /etc/network/interfaces file please?

---

### Post by MAFoElffen on 2014-12-29
For network issues, I cannot guess how your machine or local network may be configured. (Many variables there...) Please post the following info:
```

ifconfig -a
cat /etc/resolv.conf
cat /etc/network/interfaces

```
That info would be the basic info needed to start checking into your problem. Yes, your issue seems to be DNS related, but your question seeks resolution to your problem, right?

---

