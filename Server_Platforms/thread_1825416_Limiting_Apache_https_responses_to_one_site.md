---
title: "Limiting Apache https responses to one site"
date: 2011-08-15
forum: Server Platforms
---

### Post by freakyal on 2011-08-15
Hi,

I apologize in advance if this has already been covered in another thread.

Today I configured our web server to use https for our subversion site. Apache2 hosts multiple http sites and now this https site on a single IP. 

The problem is that if you try to connect to any of the hosted http sites using https you get the subversion web pages on the requested URL. Access is restricted to active directory credentials, so that limits the impact ... but it is still messy.

From what I have gathered ...
[LIST]
[*]the whole SSL thing has to happen before Apache gets the url request, so you are bound to get the cert/site-name mismatch browser error
[*]VirtualHost directives don't work with SSL because of the whole single cert per IP thing, otherwise I could create certs and SSL VirtualHosts with redirects to the http URL
[/LIST]

How can I get Apache to only serve the subversion web pages to requests that use the correct URL? Can I get it to simply ignore all other URLs? Is there a way to use redirects to point to the http site?

Much Appreciated,
Al

---

