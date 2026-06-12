---
title: "Content Security Policy nginx"
date: 2013-08-28
forum: Server Platforms
---

### Post by ConcreteDonkey on 2013-08-28
I have a server running nginx and I would like to add CSP. However I'm encountering difficulties and after following numerous guides I either get an error from nginx or they just don't work. Here is what the header looks like at the moment:

> 
add_header Content-Security-Policy "default-src 'self'; \
    script-src 'self' google-analytics.com; \
    img-src 'self' google-analytics.com;


Using this however causes nginx to report that there's an error in the config file. I want to restrict access to both myself and Google Analytics as it's the only thing I'm not serving from nginx.

---

