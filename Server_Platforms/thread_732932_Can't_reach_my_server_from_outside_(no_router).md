---
title: "Can't reach my server from outside (no router)"
date: 2008-03-23
forum: Server Platforms
---

### Post by lobsteri on 2008-03-23
I just configured my Ubuntu with Apache2, PHP and MySQL. Everything works like a charm on the server, but I can't reach it from outside. When I write the server ip address to the web browser on the server, it works just fine but from another computer it doesn't give anything. Same when I try connecting to SSH. The ip doesn't even ping.

The server is connected straight to the modem so  there are no routers to configure.

What can be wrong with that? Is there some kind of hidden firewall of somekind or what? I'm confused, as everything should be in order. I have also tried to use the Apache with different ports than 80, for example 8080, 800 and some random 1455. But it didn't have any effect on anything.

I'm running 7.10.

---

### Post by lobsteri on 2008-03-23
Solved. It was a really weird thing. I have this bridged modem that has 4 ports for computers that then get a IP from ISP's DCHP. It worked fine when I plugged a another computer in to the modem, but it didn't work when I tried through a wireless router connected to the same modem...

---

