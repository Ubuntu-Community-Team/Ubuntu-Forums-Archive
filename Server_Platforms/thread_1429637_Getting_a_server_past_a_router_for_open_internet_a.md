---
title: "Getting a server past a router for open internet access"
date: 2010-03-14
forum: Server Platforms
---

### Post by espressobeanie on 2010-03-14
I just finished setting up my small server, however I realized that no one can connect to it from the outside. The reason being is that my router is assigning internal ip's and dyndns is linked to that. I need port 80 for the Apache server, but if I have the router forward that port to my particular ip, won't it screw with everyone else's internet too? I'm not sure what to do in this situation.

---

### Post by volkswagner on 2010-03-14
Forwarding port 80 to your server's ip will not impact other pc's on your lan.  It is required for Apache to server to the outside world.

---

### Post by Iowan on 2010-03-14
As I understand it (no guarantee of accuracy), DynDNS should only affect your ability to find/access your network (router in particular) from externally. It shouldn't affect ability of internal machines to access internet.

---

### Post by espressobeanie on 2010-03-14
I see. So, I just need to find a way to punch through two routers to get to the internet. I have Verizon and they have a default firewall on your connection. Sucks that you can't shut it down.

---

### Post by lisati on 2010-03-14
To allow external access to your web site, you'll need to set up port forwarding of port 80. If the route from internet to your server goes through two routers, you'll need to do the port forwarding thing on both routers.

---

### Post by mr-woof on 2010-03-14
as said, all you need to do is forward port 80 to the ip address of your server on your router. You can test it, by going to [www.grc.com](www.grc.com) and running a shields up test.

It should show port 80 as either open (apache running) or closed (apache not running).

Have you set your server up as a static ip?

---

