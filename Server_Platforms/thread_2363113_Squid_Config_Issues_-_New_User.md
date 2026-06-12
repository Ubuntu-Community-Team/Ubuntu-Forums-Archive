---
title: "Squid Config Issues - New User"
date: 2017-06-06
forum: Server Platforms
---

### Post by wil-perry on 2017-06-06
For no other reason than I wanted to, I've decided to implement Squid (along with DHCP and DNS) on my HPE Microserver. 


All has gone well, to an extent, Squid is doing it's job and web browsing is hurtling along at a great speed, files are cached and served up very nicely indeed. 
However, I'm having issues with elements other than web browsing. 
Outlook 2016 refuses to connect to the outside world. 
Numerous (mobile and otherwise) apps refuse to play ball (youtube/whatsapp/hue/etc), also, I don't seem to be able to access a couple of webservices on the server either, virtual radar (running on 8081) and my unifi controller (8443). 


I'm not at home at the moment, so can't post a copy of the squid.conf, but will do when I get back if it helps. 


This is the first time I've tinkered with it, it's on a home setup and this is a learning experience, so the only user I'm impacting at the moment is me!
oh, btw, Ubuntu server 16.04
Any thoughts?


ETA : I'm using a proxy.pac file to configure clients to use Squid..

---

### Post by darkod on 2017-06-06
I don't have any squid experience but the first thing on my mind is HTTPS. Due to its nature (secure communications), I'm not sure HTTPS likes very much passing through proxies. Or at least you might need some additional configuration so that https is working correctly through squid.

Because Outlook these days uses https (gone are the days of rpc), other apps you mention might/probably use https or similar ssl traffic too.

So I think it comes down to that. Passing secure traffic through proxy without it thinking someone is tampering with it...

---

### Post by SeijiSensei on 2017-06-06
Squid has the capability of proxying HTTPS connections, but it requires creating a certificate on the server and trusting it on the clients.  See [http://wiki.squid-cache.org/ConfigExamples/Intercept/SslBumpExplicit](http://wiki.squid-cache.org/ConfigExamples/Intercept/SslBumpExplicit).  The Squid proxy masquerades as the origin server, and the client accepts this trick since it has a compliant certificate.

I've done some testing and gotten this to work, but I've not deployed it in a real-life setting.  My client running Squid has some 250 desktops and distributing the needed certificates hasn't been viewed yet as worth the effort.

---

### Post by wil-perry on 2017-06-07
I worked out where I was going wrong, as I'm a new user to Squid, I'd totally ignored the fact that it's an HTTP proxy and, for some reason, expected it to handle all of the traffic I threw at it. 
So now I've reconfigured my DHCP server to provide a default gateway of the perimeter router (not too concerned about that, this is a home setup after all) and option 252 is pushing the proxy.pac file for browsing. 
All of the services are now working as they should. 

The issues with FlightRadar and Unifi were coincidental, and I need to dig around a little to resolve those, but ultimately the two jobs were starting and competing for port 8080. I'll resolve that one another time.

Thanks for your thoughts.

---

