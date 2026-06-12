---
title: "linking internal http to ssl encrypted site"
date: 2011-03-28
forum: Server Platforms
---

### Post by epsolon77 on 2011-03-28
A church I've been working with has a CCTV system that has a web interface for viewing the camera feeds.  We need to see the page from the outside, but it is just an HTTP page, no encryption.  The box itself does not accept any sort of SSL encryption.  Any ideas how I can get this on the net in a secure way?

At worst I could set up a remote desktop type solution, but I was really hopping I could use some apache magic and just re transmit the page to https and ssl encrypted.

---

### Post by epsolon77 on 2011-03-28
I think I may have found something.  Hours of searching only become effective after posting a request for help...  Must be one of Murphy's laws...

[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

Does this sound right?

---

### Post by BkkBonanza on 2011-03-28
I think most proxy solutions should be able to do this. I know I can do it with Nginx (a web server like Apache) passing thru the connection. But also I'm sure Squid or other proxy software could do it and maybe with less work and resources than Apache. You would want to configure some authentication for the proxy.

---

