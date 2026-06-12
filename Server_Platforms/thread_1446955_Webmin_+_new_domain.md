---
title: "Webmin + new domain"
date: 2010-04-04
forum: Server Platforms
---

### Post by dtommy79 on 2010-04-04
Hi,

I'm just getting familiar with my new VPS.

I have webmin installed. I'd like to host more than 1 website on my server and I just can't figure out how to add a new domain (addon domain) to my server.

Any help is appreciated.
Thanks

---

### Post by Deamos on 2010-04-04
Your easiest solution would be to install Virtualmin. This will establish entire domains on your server.   

[http://www.virtualmin.com/](http://www.virtualmin.com/)

Another solution would be to manually create Virtual Servers within your Apache setup.  It isn't too hard and I am sure you can find a walkthrough on this forum.

Obviously, don't forget to create the domain from the registrar and ensure the new domains DNS info is pointing to you.  This will also work the same for subdomains.

---

