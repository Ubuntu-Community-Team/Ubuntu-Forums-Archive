---
title: "Asking about lusca sizes cache"
date: 2013-07-06
forum: Server Platforms
---

### Post by jefri new line on 2013-07-06
Hey everyone i want asking about lusca sizes cache capacity..!!!

I had used lusca proxy on ubuntu 11.10 with my specification are proc : Amd x2 2.5ghz RAM : 2Gb And Hard Drive : 320Gb..!!

And the partitions table which like :

/cache = 50gb
Swap : 4gb
/ = 266gb

but the problem was lusca stopped where cache portion only reached at 30gb and lusca cache service stopped by itself..!

in few times i was tried to start lusca again but it doesn't start the service, but if i was deleted the cache partitions and then started lusca service again with "/usr/local/squid/sbin/squid -NDd1 &" It was working..!!

My questions are..!!

1. does  anyone ever met a problem like i had..?
2. could anyone give a direction how much i could set up this configuration cache_dir aufs /cache/ 50000 87 256 in my squid.conf to according that i used 2gb ram and 320gb hdd..?

I want to use lusca again..
Thanks to all...!!

---

### Post by jefri new line on 2013-07-08
Does anyone ever used lusca as their proxy server, I really wondering to know about a good configuration to use lusca..!!

Would Someone To Help Me Please..?

---

