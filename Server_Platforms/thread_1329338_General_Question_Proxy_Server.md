---
title: "General Question Proxy Server?"
date: 2009-11-17
forum: Server Platforms
---

### Post by Jefferythewind on 2009-11-17
Hi everyone! 
  I would like to set up a simple proxy server on my home computer (USA) so that my girlfriend (in China now) can access facebook.  I have never set up a proxy server before.  I guess the idea is that she should be able to connect to the internet through my computer.  Is that right? 
  I have been using Ubuntu for a few years now and i feel pretty confident setting up new software, i just don't know which software to use and which direction to go to do this.  Could someone recommend something to me?  I have heard of squid and eBox, would these do what i want them to do?

Thanks in advance for any suggestions!

---

### Post by LinGNUbie on 2009-11-17
IF by "connect through your computer" means from physically near your computer then you could simply install a router (with wifi?) to share the connection. Ultimately you could use the box (with proxy server) to provide a connection, but you would still need a second NIC installed in the box to provide the connection to her computer.

---

### Post by kewlrichie on 2009-11-17
I guess you could make a proxy but I think a VPN might be a better choice she would VPN in and use your gateway to surf the web? No ?

---

### Post by Jefferythewind on 2009-11-18
I was just thinking a VPN might be a better choice.

When i wrote use the internet "through" my computer, i didn't mean the user would be close to my computer.  She is on the other side of the world.  I guess i don't know exactly how proxy servers work.  I think i will try to use a VPN  first and then try to learn more about proxy servers.

thanks

---

### Post by bm.mol on 2009-11-18
In principle a proxy server does 3 things:
1. It controls incoming traffic (e.g. webtraffic) and reroutes (to the webserver)
2. It controls outgoing traffic (access to the internet from internal clients)
3. It controls the amount of incoming traffic by means of a cache. Frequently visited websites are stored, so they don't need to come from the (slow) internet. It also delivers data from cache from the internal webservers, so that the load on the webservers is minimised.

---

