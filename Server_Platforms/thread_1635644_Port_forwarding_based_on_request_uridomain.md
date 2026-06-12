---
title: "Port forwarding based on request uri/domain"
date: 2010-12-02
forum: Server Platforms
---

### Post by artheus on 2010-12-02
Hey. I've been googling for how to set up (if it's even possible) a port redirect based on the request uri or requested domain name.

So if someone request the domain [www.domain.com:80](www.domain.com:80), my first server will redirect this to the local ip 192.168.100.15:80, but if the request is phpmyadmin.domain.com:80, the request goes first to my external ip, as usual. But internally that will be forwarded to 192.168.100.92:80 instead of 192.168.100.15:80.

Or if someone might request domain.com:336 that could be port forwarded to 192.168.100.45:1166.

(This is just sample ports and domains, to illustrate what I want)

I want this because my ISP won't provide static external ip-s.

Cheers,
Artheus

---

### Post by artheus on 2010-12-02
I've seen that I could use mod_proxy for the port 80. But my worry is other ports for eg. FTP, VPN, Mail etc.
I have got several servers hosting different things, And I'm going to move, and when I move I have to change ISP. So there won't be static IP's no more.

Hoping for fast answers.

Cheers,
Artheus

---

