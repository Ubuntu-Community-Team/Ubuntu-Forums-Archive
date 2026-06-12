---
title: "Web sites without WWW."
date: 2005-08-20
forum: Server Platforms
---

### Post by Mr. Electric Wizard on 2005-08-20
Can you guys tell me what the significance of this is?
I understand how a normal domain works in regards to a Web Server, but what is the significance when the top level domain is:
[http://www.somewebsite.com](http://www.somewebsite.com), and
 
there is link on the page that points to:
[http://forums.somewebsite.com](http://forums.somewebsite.com)

What is the significance of the "www" being missing, and being replaced with "forums"?

---

### Post by heimo on 2005-08-20
It's the hostname part, you can have [www.example.com]("http://www.example.com") pointing to another server than forums.example.com, which adds flexibility. Sometimes it's easier to add forum software on it's own name virtual host. www is just a convention for default web server on that particular domain.
[http://en.wikipedia.org/wiki/FQDN]("http://en.wikipedia.org/wiki/FQDN")



EDIT: Terrible hangover.

---

### Post by nad on 2005-08-20
As with any fully qualified domain name, the first field is the hostname of the computer on the network. The link may be directing your request to another server (or virtual server).

With the advent of server clusters, farms, load balancing and virtual addresses this is no longer necessarily true, however, convention has been that the public server opened to port 80 is named www.

---

