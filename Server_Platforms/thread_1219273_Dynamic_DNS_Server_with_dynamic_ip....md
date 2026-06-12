---
title: "Dynamic DNS Server with dynamic ip..."
date: 2009-07-21
forum: Server Platforms
---

### Post by jonathanmotes on 2009-07-21
Yeah, so is this possible? I have several *dynamic* domains that point to a single web server. I am trying to get away from depending on an external DynDNS service for them (currently using everydns.com). 

I want the DNS server to exist on the same network as the web server (hopefully on the same server).

I realize that I will have to utilize an external DNS service for the DNS server's domain (since the server's domain needs to be dynamic itself). I don't mind using [http://www.dyndns.com/](http://www.dyndns.com/) for it (they are reliable - so I don't mind using them, they just don't offer the free support that I need for my other domains.)

I hope this is not too confusing....just let me know if something needs more explaining. I guess I just need some way to query a service like [http://myip.dnsomatic.com/](http://myip.dnsomatic.com/), then update the ip's for the domains.....

Thanks!

---

### Post by strujillo.jr on 2009-07-21
This is exactly what I want to do. Eliminate the middle man and just do the DNS myself...I know there is something like Bind 9 or something but im not sure. I shall be watching this forum :popcorn:

---

