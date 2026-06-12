---
title: "Knowing which httpd package to install?"
date: 2008-03-15
forum: Server Platforms
---

### Post by drachs on 2008-03-15
I am new to ubuntu and am trying it out on a server. I have a problem though, sometimes what I want comes in more than one package, and I don't know how to get guidance about which one to consider "default".

For example:

root@devserver:/var/www# apt-get install httpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package httpd is a virtual package provided by:
lighttpd 1.4.18-1ubuntu1.2
apache2-mpm-itk 2.2.3-04-3build4.1
apache2-mpm-worker 2.2.4-3ubuntu0.1
apache2-mpm-prefork 2.2.4-3ubuntu0.1
apache2-mpm-event 2.2.4-3ubuntu0.1
yaws 1.68-3ubuntu1
webfs 1.21-5
tntnet 1.6.0-2
thttpd 2.23beta1-7
roxen4 4.0.425-6ubuntu1
mzscheme 1:360-1ubuntu1
mini-httpd 1.19-4
micro-httpd 20051212-6
mathopd 1.5p5-1
fnord 1.10-2
ebhttpd 1:1.0.dfsg.1-1
dhttpd 1.02a-16
cherokee 0.5.6-1
caudium 2:1.4.9.1-3
bozohttpd 20060517-5ubuntu1
boa 0.94.14rc21-2
aolserver4 4.5.0-10ubuntu2
You should explicitly select one to install.
E: Package httpd has no installation candidate

How do a pick one? I just want plain jain web server capabilities with support for php and postgresql. Nothing wierd.

(Sorry this is a repost, but I messed up the topic for the last post, it was not indicative of my problem, and the forum software wouldn't let me edit it)

---

### Post by MJN on 2008-03-15
You've just happened upon a so-called virtual package (httpd describing generic web server functionalities hence it is not a package itself).

In this instance, I suggest installing the Apache (v2) web server as it is pretty much the 'industry standard' and hence you'll find yourself in good company regarding support etc.

Hence, try [B]sudo apt-get install apache2

[/B]Mathew

---

### Post by FakeOutdoorsman on 2008-03-15
This will get you pointed in the right direction:
[Installing Apache, PHP, and mySQL]("https://wiki.ubuntu.com/ApachePHPMySQL") at Ubuntu Wiki

---

