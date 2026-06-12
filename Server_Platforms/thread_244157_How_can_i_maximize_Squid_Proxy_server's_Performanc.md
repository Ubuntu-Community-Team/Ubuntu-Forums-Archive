---
title: "How can i maximize Squid Proxy server's Performance"
date: 2006-08-26
forum: Server Platforms
---

### Post by CameronCalver on 2006-08-26
I have just set up squid on my proxy server and i think it is great.
I have the cache_mem set to 32mb and maximum size set to 150mb but i would like to boost the performance my computer is not the greatest it is intel celetron 500mhz with 390mb ram and i run ubuntu on cli only so it should not take up all that much ram so what should i put my cache_mem up to and does anyone have any suggestions to improve the performance i am open to suggestions and i will post my squid.conf if neccesary

---

### Post by Woei on 2006-08-26
> **CameronCalver said:**
> I have just set up squid on my proxy server and i think it is great.
I have the cache_mem set to 32mb and maximum size set to 150mb but i would like to boost the performance my computer is not the greatest it is intel celetron 500mhz with 390mb ram and i run ubuntu on cli only so it should not take up all that much ram so what should i put my cache_mem up to and does anyone have any suggestions to improve the performance i am open to suggestions and i will post my squid.conf if neccesary

How many clients does that proxy serve ? What is its connection speed to the internet ? If it's just you behind it on a residential xDSL/cable modem, there's no need to tweak anything further, as even with the default settings that machine will have horsepower to spare.

Moreover, cache_mem is *not* the maximum amount of memory Squid will use. It's only a measure for the amount of popular files that will be kept in memory at all costs. So I'd reckon you can even bring the maximum down a little.

---

### Post by Abhi Kalyan on 2007-01-28
[http://www.ubuntuforums.org/showthread.php?t=320733&highlight=squid](http://www.ubuntuforums.org/showthread.php?t=320733&highlight=squid)

---

### Post by CameronCalver on 2007-01-28
im sorry guys but i have already solved this problem

---

