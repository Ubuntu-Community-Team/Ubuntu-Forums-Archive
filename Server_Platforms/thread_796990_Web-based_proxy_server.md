---
title: "Web-based proxy server"
date: 2008-05-16
forum: Server Platforms
---

### Post by Narpas on 2008-05-16
Hey, I'm trying to get around a websense-style blocker by using my home server as a web-based proxy. The ultimate goal is to get http://narpas.ath.cx<XXXX>[http://google.com](http://google.com) to serve up a mirror of google. I've tried working around with squid3, but the closest I've gotten with that is [http://www.narpas.homelinux.com:3128/](http://www.narpas.homelinux.com:3128/) and I can't quite figure out if I've got an issue with configuration, with my understanding of what squid does, or if I just haven't figured out the correct way to put in the URL.

I know that my post is rambling, so executive summary: what programs / protocols should I look at if I want to punch in a URL and have my home server mirror that up for me?

---

### Post by Donb01 on 2008-05-16
I blew websense out of the water with squid because my personal IP has no reason to be in its proxy database.  They got rid of websense now and they route all our web traffic through a proxy which they force on you using an MS Active Directory Group Policy.  It's really too bad that firefox ignores it ant they're too stupid to figure that out :D

You need to make sure that the IP that your system sees coming from work is allowed to access your proxy server.  In my case it was locked down by default and I had to add the work IP.  Then you need to go into your browser of choice, under connection settings, put in your IP for proxy and 3128 for the port.  It is also wise to tell it not to proxy things on the local network.

I also preferred administering squid via webmin rather than any other way.

---

### Post by bapoumba on 2008-05-17
It is not our policy to support requests that may infringe local rules. Please see with your network admins. Thread closed.

---

