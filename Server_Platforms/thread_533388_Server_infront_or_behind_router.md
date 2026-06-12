---
title: "Server infront or behind router?"
date: 2007-08-23
forum: Server Platforms
---

### Post by chainzawz on 2007-08-23
Hello all, I know that this has been posted before but I think this may be a different kind of situation.  Anywho I have an old computer at home that I will be installing Unbuntu Server 6 onto. I will be using the computer for basic file storage for my home network.  


As of right now I have a cable modem which a cable line comes into and then that goes to a router which in turn goes to the one window laptop and one macbook that I have.  As of right now the desktop which I will be using as the server will be connected to the internet through the router.  Is this the way it should be or should it be before the router?

---

### Post by steveneddy on 2007-08-23
> **chainzawz said:**
> Hello all, I know that this has been posted before but I think this may be a different kind of situation.  Anywho I have an old computer at home that I will be installing Unbuntu Server 6 onto. I will be using the computer for basic file storage for my home network.  


As of right now I have a cable modem which a cable line comes into and then that goes to a router which in turn goes to the one window laptop and one macbook that I have.  As of right now the desktop which I will be using as the server will be connected to the internet through the router.  Is this the way it should be or should it be before the router?

Behind the router.....

---

### Post by southernman on 2007-08-23
The best way to do it is setup a two router system.

See the attached image from Steve Gibson's website:

edited... see steveneddy's reply if you don't have a spare box or another router laying around.

---

### Post by rickyjones on 2007-08-24
Well, I see two main ways to set it up.

1) **The Easy Way.** Put the server behind your router with the rest of your network. Only forward the ports you need open to that machine. Make sure it has a static IP address. *This is the way I do it 90% of the time for personal use and for small business clients.*

2) **The Secure Way.** Use two routers. Cable modem goes to the first router, which your server and the second router connects to. The downside is that it is a little more complicated and costly in the beginning. But, it would definitely be more secure.

Hope this helps!

-Richard

---

