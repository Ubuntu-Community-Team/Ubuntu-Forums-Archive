---
title: "Accessing Websever WAN IP from in the same LAN !Help!"
date: 2010-07-21
forum: Server Platforms
---

### Post by ubila on 2010-07-21
Hello, 
 
So i run a ubuntu 8.10 server setup for webhosting. I have my router portforwarding to my servers LAN IP, and i have DNS setup and pointing to my WAN IP.
 
My host entries are all setup on ubuntu also.
 
The problem :
I can access my server from typing WAN IP address or any of the URLS with webpages hosted on the server, all seems to be working.
BUT, i can only access these from OUTSIDE my network. If i try access them within my LAN, i get sent to my routers login page.
 
I really cant find anything that could be causing this....
Any ideas would be greatly appreciated.
 
Regards
Richard

---

### Post by ubila on 2010-07-21
After more reading it would seem this is because my router does not have line loopback??
 
A temp fix i have added the web-address to my hosts file pointing to the server and that works. But i dont want to have to do this for each website i host!
 
Can anyone confirm that this IS infact because my router does not have line loopback?

---

### Post by stevenvegt on 2010-07-21
[LEFT]    The problem as I see it is that you use a consumer grade router to host some sites. So far so good and it can be done, but never expect it to work comfortable.
  You have your WAN port and your LAN ports (possibly 4 of them) the LAN ports are switched whereas the WAN port sits in another network and is thus routed. 
  When you come from the outside you enter the WAN port and the forward is executed and you get your website. When you come from the LAN side you are already past the point where the routing would take place, so you get your routers interface and not the webpage.
  A local loop interface will not help you accessing your LAN via the WAN port
  [/LEFT]

---

### Post by cdenley on 2010-07-21
That is a very common limitation with routers. Some routers will use port forwarding rules for traffic received on a LAN port destined for its own WAN IP. Some will not. Some actually have a configuration option to enable this. Usually you have to workaround the problem either using entries in your hosts file, or configuring a DNS server on your LAN to resolve your domains to the LAN IP.

---

### Post by ubila on 2010-07-21
Yea, its unfortunate i suppose, since if i use the host file i wont know if its actualy working on the WAN unless i check on a different network.
 
I do have a cisco 2600 router, maybe i could hang that off the home router ? Would solve the problem since all requests would end up going through that router even on LAN? (im just going to have to get out the cisco books and try remeber how to program it haha)

---

### Post by cadriel on 2010-07-22
If I'm reading this correctly, you want your domain to work inside and outside of your local LAN.

I.e., mydomain.com should work in any location.

If so - I had this problem and it turned out to be an easy one to resolve. But only if your router supports it.

My consumer grade LinkSys router allows me to circumvent this by adding a custom DNS entry. My router calls it something obscure (of which I can't remember the name right now). But, the first thing I'd do is check out your router interface and look for options that allow you to define a domain name and IP address.

The other option I researched was adding a custom DNS on my LAN and using that to resolve the issue instead. But that sounded like far too much work for something so simple. DNSMasq would be a good option here if your router doesn't support what you need. It's easy to setup and is actually what a lot of routers run anyway.

Hope that helps.

---

