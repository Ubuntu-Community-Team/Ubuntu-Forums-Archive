---
title: "Just want to set up a simple web page"
date: 2005-02-14
forum: Server Platforms
---

### Post by Mike Nasvadi on 2005-02-14
I have searched these forums but I just can't find the right info on how to set up a simple web page.  I don't need php, or anything fancy.  I just want to host some images and an html file.  Can anyone point me in the right direction?

---

### Post by cblack on 2005-02-14
You'll want to install a webserver, the most popular or which is Apache. Apache can be installed via apt-get or whichever program you use to install packages in Ubuntu. More info on apache is available [http://www.apache.org](http://www.apache.org).

---

### Post by az on 2005-02-14
sudo apt-get install apache2
Everything you want to put on the net will be in /var/www.

To make a directory the default, change the redirect in /etc/apache2/sites-enables/default.

There are many content management systems out there (that use php) that can make your life a lot more easy, especially if you just want to share some photos with the family.  For example, you can upload photos to your web page from any computer.  You can do a lot of stuff.  It is just a ferw keyclisks away.
sudo apt-get install php4 mysql-server (for starters)

Do you have a static ip address?  If not, you should investigate dynamic dns.  You can even go to Easy dns and register a dns and have dynamic dns client use that domain name for you.  I think that only costs 35 bucks. Otherwise, it is free, but you have to use certain domain names.

---

### Post by rufius on 2005-02-14
[QUOTE=Mike Nasvadi]I have searched these forums but I just can't find the right info on how to set up a simple web page.  I don't need php, or anything fancy.  I just want to host some images and an html file.  Can anyone point me in the right direction?[/QUOTE]
 Apache may be a bit overkill for what you want, take a look at dhttpd and bozohttpd. They're small secure web-servers with easier config setups, and especially dhttpd should be of interest since its not designed to work with cgi support and you only wanted html so I'd say that'd be your best bet.

---

### Post by Mike Nasvadi on 2005-02-14
Excellent.  I was able to install Apache without a hitch.  You can check out the page at [www.asobiketour.com](www.asobiketour.com) if you wish.

How hard is it to host my own domain name?

---

### Post by Mike Nasvadi on 2005-02-14
[QUOTE=azz]sudo apt-get install apache2
Everything you want to put on the net will be in /var/www.

To make a directory the default, change the redirect in /etc/apache2/sites-enables/default.

There are many content management systems out there (that use php) that can make your life a lot more easy, especially if you just want to share some photos with the family.  For example, you can upload photos to your web page from any computer.  You can do a lot of stuff.  It is just a ferw keyclisks away.
sudo apt-get install php4 mysql-server (for starters)

Do you have a static ip address?  If not, you should investigate dynamic dns.  You can even go to Easy dns and register a dns and have dynamic dns client use that domain name for you.  I think that only costs 35 bucks. Otherwise, it is free, but you have to use certain domain names.[/QUOTE]


Hey I must have skipped reading this before I posted my latest reply.  Now that i have Apache up and running I will investigate some Php stuff.  Anyway the later part of what you posted is what I would like to do.  I do have a static IP, and would like to host my own domain name -- bunches of them if possible.

---

### Post by az on 2005-02-14
easydns

---

### Post by Circle of Owls on 2005-02-16
I've been using DynDns.org for several years, and have been very happy with them. I believe that they are one of the most popular domain hosting services. Here is their page on setting up a custom domain name on a static IP: 

[http://www.dyndns.org/services/custom/](http://www.dyndns.org/services/custom/)

It looks like it runs about $25/yr. 

Here is a great starting place for PHP: 

[http://www.hotscripts.com/PHP/Scripts_and_Programs/index.html](http://www.hotscripts.com/PHP/Scripts_and_Programs/index.html)

These are prebuilt scripts, in most cases they will have very little setup required, and many of them are Free. You may want to look into a photo album, since you are hosting an image library. Nice site, btw.

---

