---
title: "change default www folder"
date: 2009-02-24
forum: Server Platforms
---

### Post by jdcnosse on 2009-02-24
Hi all, I can't seem to remember how to change the default document root folder for apache.  I knew that I had done it before though...

Basically what I want is for /var/www to be able to be /home/james/www and still work with Apache2.

---

### Post by spiderbatdad on 2009-02-24
Hi. This is usually set as DocumentRoot in the file /etc/apache2/sites-available/default...A good practice is to copy the default site to another file, you might call my-site. And edit that file. Use sudo a2dissite default && sudo a2ensite my-site to disable the default site and enable my-site. Additionally the directory configurations in your vitual host file get changed. Check this out for more info:
[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by williane on 2009-02-24
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1)

is a pretty quick how-to I like. Actually all the slicehost articles by PickledOnion are really good imo.

---

### Post by jdcnosse on 2009-02-24
Thank you, that helped a lot.

---

