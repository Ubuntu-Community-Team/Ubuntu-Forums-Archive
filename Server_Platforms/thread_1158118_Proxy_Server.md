---
title: "Proxy Server"
date: 2009-05-13
forum: Server Platforms
---

### Post by dbuttera187 on 2009-05-13
Hey everyone, I am trying to set up a proxy server (apt-cacher) kind of deal but a little different than normal. The normal source.list file on any of the hosts usually looks something like this:
 
"deb http://www.websitehere.com/yadayadayada"
 
I want to route the source through my proxy server. The difference is, I want to route it through the proxy server and into a local directory on it. So the normal local source line would look like this:
 
"deb file:/usr/local/mydebs"
 
I want it to route through the IP of the proxy server somehow first and into the local directory on the proxy server. Anyone?

---

