---
title: "webmin question about bandwidth limiting"
date: 2006-07-08
forum: Server Platforms
---

### Post by dccool879 on 2006-07-08
I want to make my linux box into a router. I hear you can use webmin to do this. I was wondering if I could configure it to limit the bandwidth to 30 KB/s upload for all the computers EXCEPT the router which is for vonage phone. I want to do this because if my family uses too much bandwidth, the vonage phone will disconnect or skip. i have a 48 KB/s (384 kbit) upload total, so i want to reserve 18 KB/s for the phone. Is this possible?

---

### Post by crmanski on 2006-07-09
What type of traffic are you trying to limit? WWW, FTP, bittorrent?

Webmin provides a good module for squid, which can be setup transparently and also use delay pools to limit the throughput.
[http://www.squid-cache.org/Doc/FAQ/FAQ.html#toc19.8](http://www.squid-cache.org/Doc/FAQ/FAQ.html#toc19.8)
This will not cover p2p programs though. For that you would need to implement traffic shaping, which is not easy.  There is some info on this here...
[http://www.shorewall.net/traffic_shaping.htm](http://www.shorewall.net/traffic_shaping.htm)
The above refers to...
[http://www.lartc.org/](http://www.lartc.org/)
Shorewall is in the repositories.

---

### Post by dccool879 on 2006-07-13
i want to limit all internet activity. Also, can i limit the number of connections at once? my brother is a bandwidth hog (need to take him to a psychiatrist), and i just want to play online games without him and the phone sucking up all 384 kbits of our upload.

---

### Post by crmanski on 2006-07-15
> **dccool879 said:**
> i want to limit all internet activity. Also, can i limit the number of connections at once? my brother is a bandwidth hog (need to take him to a psychiatrist), and i just want to play online games without him and the phone sucking up all 384 kbits of our upload.

I did a search of the forums and I think you might want to try this...
[http://ubuntuforums.org/showthread.php?t=25911&highlight=limit+upload](http://ubuntuforums.org/showthread.php?t=25911&highlight=limit+upload)
It refers to this...
[http://lartc.org/wondershaper/](http://lartc.org/wondershaper/)
and it is in dapper...
[http://packages.ubuntu.com/dapper/net/wondershaper](http://packages.ubuntu.com/dapper/net/wondershaper)

---

