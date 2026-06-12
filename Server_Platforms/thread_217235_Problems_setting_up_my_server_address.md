---
title: "Problems setting up my server address"
date: 2006-07-16
forum: Server Platforms
---

### Post by sdphantom6 on 2006-07-16
I followed the LAMP server install and have read the [Ubuntu server guide.]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html")

On my laptop (which is connected via a router to the internet and my ubuntu box) I don't know what address to use to reach the server. When I go to /etc/hosts I get the following IP's
127.0.0.1
127.0.1.1
which don't seem ot work when I try to use the SSH or my browser.
Basically I want to know how to setup the server so that I can point a remore SSH or browser to the server. (HTML would point into the /var/www/ folder?)

---

### Post by Randomskk on 2006-07-16
127.0.0.1 is a local address, which means whatever computer you use it on it'l point to the current computer.
From your server, type in "ifconfig eth0" and look for where it says IP address, and it will PROBABLY be something like 192.168.0.3, then go to this on your laptop.

---

