---
title: "Varnish and Memcached"
date: 2013-05-24
forum: Server Platforms
---

### Post by marwan83 on 2013-05-24
hi,



Would anyone help me please configure Varnish to use Memcahced? Both on the same server. Memcahced is using all default configuration. I'm not very much aware of Varnish extensions.



Please help.

---

### Post by sandyd on 2013-05-24
[https://github.com/sodabrew/libvmod-memcached#installation](https://github.com/sodabrew/libvmod-memcached#installation)

---

### Post by marwan83 on 2013-05-24
> **sandyd said:**
> [https://github.com/sodabrew/libvmod-memcached#installation](https://github.com/sodabrew/libvmod-memcached#installation)
Thanks a lot Sandy. I have seen that. But im not very much sure what to do. I dont have GNU Autotools installed. So how to get GNU Autotools installed? Whats next to be done after GNU Autotools installed?

---

### Post by sandyd on 2013-05-25
Just install
```

sudo apt-get install build-essential
```
should install autotools.

FYI, I think that the memcached module will only work when is compiled **along** with Varnish - meaning that you will have to compile Varnish as well.

Personally, I think that Varnish is already top of the performance without adding anything extra. Most of the other things will have to do with how the page actually loads things (See Google Pagespeed for Apache, and Google Pagespeed for Nginx which is in my signature), and technologies such as SPDY (for SSL). Compressing the page and/or using a CDN to reach places that your server is far from also helps.

A setup like Varnish -> Nginx -> php5-fpm (xcache) is already quite fast if Varnish is tuned properly (i.e. stripping cookies where appropriate to allow Varnish to cache things) as Varnish serves from memory

---

