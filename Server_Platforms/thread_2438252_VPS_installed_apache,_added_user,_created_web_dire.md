---
title: "VPS: installed apache, added user, created web directory,p...but site won’t load"
date: 2020-03-08
forum: Server Platforms
---

### Post by cnedas on 2020-03-08
Hello,

This regards configuration for a real live site configured on VPS with Ubuntu Server 18.04 and Apache2

I created a user, created a directory for the new website wirhin /var/www/html/mysite/, created vhost with ServerName and DocumentRoot pointing to /mysite/

In /etc/hosts I added and modified IP for localhost

myserverip mysite
myserverip localhost 

At my registrar I added the server IP and modified ns1. and ns2 more than 48 hours ago, but my site still won’t load.

**Do I have to modify DNS and add ns1. and ns2. anywhere within Ubuntu server?**

Thanks in advance

---

### Post by TheFu on 2020-03-08
Perhaps this explanation will help: [https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site](https://blog.jdpfu.com/2010/11/05/what-you-need-to-have-a-web-site)

---

