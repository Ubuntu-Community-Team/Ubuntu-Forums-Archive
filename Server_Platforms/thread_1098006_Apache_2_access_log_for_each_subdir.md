---
title: "Apache 2 access log for each subdir"
date: 2009-03-16
forum: Server Platforms
---

### Post by Mordachai on 2009-03-16
Ive setup an apache 2 webserver containing several virtual hosts. Now on one of the hosts I want a subdirectory that has a different access log then the rest of that virtual host (its a site with multple tools who need different access logs)

Is this possible?

---

### Post by bodhi.zazen on 2009-03-16
Yes, specify a log file in your Virtual Host.

I personally make a separate log for each virtual host, makes it easier if there are problems.

---

### Post by Mordachai on 2009-03-16
I already have an accesslog for my virtual host. I just want a separate accesslog for a subdirectory of that virtual host. So if my vhost is located in /var/www/vhost1, I want a separate accesslog for anything going to /var/www/vhost1/subdir1.

---

