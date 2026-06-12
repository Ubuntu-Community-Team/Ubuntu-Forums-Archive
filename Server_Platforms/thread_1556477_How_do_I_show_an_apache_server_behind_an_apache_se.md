---
title: "How do I show an apache server behind an apache server?"
date: 2010-08-19
forum: Server Platforms
---

### Post by Keymaster on 2010-08-19
I have servera.domain.internal which has port 80 forwarded to the web as example.com
I have serverb.domain.internal which I want to forward on port 80 as subdomain.example.com

How do I setup the virtual host on the internet exposed servera? Thanks

PS: This is ubuntu 8.04

---

### Post by arrrghhh on 2010-08-19
Just had some interesting conversation with another individual about this not too long ago...

I'm no expert on vhosts or apache, but here's some good documentation.

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

---

### Post by Keymaster on 2010-08-19
Thanks. I've actually decided to use a non-standard port anyway as it is simply for a status screen that the general public can't access anyway.

---

