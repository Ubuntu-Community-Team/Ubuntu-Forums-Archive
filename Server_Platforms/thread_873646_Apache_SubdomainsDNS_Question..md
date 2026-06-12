---
title: "Apache Subdomains/DNS Question."
date: 2008-07-29
forum: Server Platforms
---

### Post by bobbocanfly on 2008-07-29
I am part of a project that will give free hosting (including a subdomain address) to members of the FOSS community, based completely on free software.

I am planning to setup users subdomains using Apache mod_rewrite (like [http://muffinresearch.co.uk/archives/2006/08/20/redirecting-subdomains-to-directories-in-apache/](http://muffinresearch.co.uk/archives/2006/08/20/redirecting-subdomains-to-directories-in-apache/)).

Will I need to register each new subdomain with a DNS server in order to make this work? Ideally i wouldnt have to and could just say send anything with ubuland.org in it to my server where Apache sorts out subdomains etc. with mod_rewrite. Is this possible? If not what is the best way to do this?

Thanks!

---

### Post by MJN on 2008-07-29
All you need is a wildcard DNS entry. In BIND this would take the form:
 
```
*.ubuland.org. IN A <IP ADDRESS>
```Connecting clients will send the requested HOST to the server as part of the HTTP request hence you can use your mod_rewrite to redirect internally (e.g. [http://somehost.ubuland.org](http://somehost.ubuland.org) --> [http://ubuland.org/somehost](http://ubuland.org/somehost))
 
Mathew

---

### Post by bobbocanfly on 2008-07-29
> **MJN said:**
> All you need is a wildcard DNS entry. In BIND this would take the form:
 
```
*.ubuland.org. IN A <IP ADDRESS>
```Connecting clients will send the requested HOST to the server as part of the HTTP request hence you can use your mod_rewrite to redirect internally (e.g. [http://somehost.ubuland.org](http://somehost.ubuland.org) --> [http://ubuland.org/somehost](http://ubuland.org/somehost))
 
Mathew

Thanks. Didnt think it was going to be that simple :D

---

