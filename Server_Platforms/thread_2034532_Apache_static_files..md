---
title: "Apache static files."
date: 2012-07-28
forum: Server Platforms
---

### Post by sandyd on 2012-07-28
Ive been using nginx on my sites for a while now, and with all the trouble Ive gone through, im thinking of moving back to Apache.

There are a few things I am curious about though.

a) Apache is known to serve static files slower, and nginx serves static files the fastest.

I currently have Varnish stationed in front of everything. 

Does that mean that I should generally retain most of the serving speed (req/s) if varnish caches those files?

b) I currently use a seperate-user php-fpm setup, where each user gets their own socket, so that php can access each user's files.

How can I accomplish this in Apache?

---

### Post by sandyd on 2012-07-30
bump

---

### Post by Lars Noodén on 2012-07-30
For a) could you test the difference between Apache with and without Varnish acceleration using ab?

[https://httpd.apache.org/docs/2.2/programs/ab.html](https://httpd.apache.org/docs/2.2/programs/ab.html)

That way you could be sure.  I would not expect the difference to be big for static pages.  You might be able to save traffic with [mod_deflate](https://httpd.apache.org/docs/2.2/mod/mod_deflate.html), but that might increase the load on the server.

---

### Post by sandyd on 2012-07-31
The pages are not static. There are a few php-based sites.

Ive already tested apache without varnish - it was deadly slow, and the reason why I moved to nginx, then later varnish + nginx.

Ill test apachebench tomorow.

Thanks!

---

### Post by SeijiSensei on 2012-07-31
Just curious, but how many requests per second do you average?  I've built a number of sites, none of which have ever displayed performance issues with Apache+PHP+PostgreSQL.  Of course even my busiest sites only handle a few thousand requests per day. 

> b) I currently use a seperate-user php-fpm setup, where each user gets their own socket, so that php can access each user's files.

How can I accomplish this in Apache? 

If the users have unique virtual hosts, then give each user a website directory under /home/user with 755 permissions and make that the DocumentRoot in the corresponding <VirtualHost> container.  You'll have to change the default permissions on /home/user from 700 to 711 so the Apache pseudo-user "www-data" can see the website directories.

---

