---
title: "Apache2 default virtual server"
date: 2009-04-18
forum: Server Platforms
---

### Post by botfish on 2009-04-18
Hi,

I've set up a number of Apache2 virtual servers.

In /etc/apache/sites-available I have
a-sub-domain.domain.com
domain.com

"a-sub-domain.domain.com" is processed first so it becomes the default site for my ip address. i.e. request [http://ip-address/](http://ip-address/) from a browser and I get a-sub-domain.domain.com

I would like domain.com to be the default site for my ip address. Any ideas on how to do this with out changing the file names of my virtual host containers?

Cheers

---

### Post by brianhenson on 2009-04-19
botfish,

try renaming the file to something like z-subdomain or moving the subdomain to the end of the file if you only use one file for domains.  


Brian

---

### Post by Thirtysixway on 2009-04-19
> **brianhenson said:**
> botfish,

try renaming the file to something like z-subdomain or moving the subdomain to the end of the file if you only use one file for domains.  


Brian

That's what I did for my server.  Move the one you want default to the top of the file, as the first entry.

---

