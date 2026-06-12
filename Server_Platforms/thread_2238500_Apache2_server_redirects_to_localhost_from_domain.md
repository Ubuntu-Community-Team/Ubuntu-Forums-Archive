---
title: "Apache2 server redirects to localhost from domain"
date: 2014-08-08
forum: Server Platforms
---

### Post by gundulf on 2014-08-08
Hey there.

So I set up my apache2 web-server to work with owncloud and it works fine in my local network ( access through server-ip/owncloud ).
But if I want to access the owncloud dir via my domain im redirected from domain.com/owncloud to localhost/owncloud , from every machine I tried on.

So can anyone tell me, how I can get my webserver to a) not redirecting to localhost/owncloud and b) make access fromd domain.com/owncloud possible.
Hope my problem is understandable ...

---

### Post by koenn on 2014-08-08
no web server I know of would do such redirects all by itself so if you haven't put any redirection logic there yourself (in apache conf); this probably means that your owncloud  is doing this, i.e. that somehere in the config is a statement that makes owncloud think its  servername is "localhost", causing owncloud to generate links   (or maybe even actual redirects) to URLs starting with [http://localhost/owncloud](http://localhost/owncloud) ...  

or in other words : review your owncloud config.

---

### Post by Deuce1912 on 2014-08-09
This link should be of some assistance. 

[http://forum.owncloud.org/viewtopic.php?f=26&t=20086](http://forum.owncloud.org/viewtopic.php?f=26&t=20086)

---

### Post by Chuong_Pham on 2014-08-10
Hi guys, thank you for your time. I eventually solved the problem by "Require local" and "Require 192.168.2.1/24" and I also added my site to hosts file in my laptop to test with 3G and Wifi

---

