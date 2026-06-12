---
title: "ligHTTPd Web Server gaining ground"
date: 2007-06-29
forum: Server Platforms
---

### Post by warcriminal on 2007-06-29
I saw this article about ligHTTPd web server.  Apparently it's gaining ground on other web servers, has anyone tinkered with it?

[http://www.goitexpert.com/entry.cfm?entry=ligHTTPd-High-Performance-High-Availability-Web-Server](http://www.goitexpert.com/entry.cfm?entry=ligHTTPd-High-Performance-High-Availability-Web-Server)

Any thoughts?

---

### Post by glenndavy on 2007-06-29
I havent, but I believe a fair few people using ruby on rails and assorted python web frameworks use it - if you're hunting for information and experperiences, that might be a place to start looking.

---

### Post by WesRatcliff on 2007-06-29
I run it exclusively at our colo for serving up flat files on high-traffic sites. It screams.

I've also got two instances of it in front of a couple PHP boxes doing load balancing.

It's not a silver bullet, but what it does, it does well.

Wes

---

### Post by Frosty Cold Drink on 2007-06-29
Lighty is quite nice. It doesn't have quite the feature list Apache has (including available modules, of course), but ow often does one implement those features anyway? Waste not, want not.

---

### Post by elst on 2007-06-29
I switched a server from Apache with mod_python to lighttpd with FastCGI a while ago, and have been quite impressed - lighttpd uses less memory, and configuration feels tidier (if you get regular expressions). Performance seems good. One of the applications on the server doesn't seem quite as happy with FastCGI as with mod_python; I suspect that FastCGI support was less tested, as FastCGI has been out of fashion.

---

### Post by gaten on 2007-06-29
Lighttpd is great. Small, stable, secure and fast. VERY easy to chroot. But, like mentioned above, it doesn't have all the cool modules APache does (I miss mod_security). But once it gets more popular, we'll start to see more things for it popping up.

---

