---
title: "apache"
date: 2007-10-24
forum: Server Platforms
---

### Post by tynen on 2007-10-24
I need help setting up Apache, and solely Apache. I don't need a full LAMP server. I'm going to be hosting a plain text HTML website. I searched for how to set up Apache but all i find is full LAMP server install guides.. Can someone possibly help or point me in the right direction?

---

### Post by twistedtwig on 2007-10-25
could you not just ignore the PHP mysql, perl, etc parts of the install?

---

### Post by robert_pectol on 2007-10-25
```
sudo apt-get install apache2
```
Simple!

---

### Post by jenhsun on 2007-10-25
> **tynen said:**
> I need help setting up Apache, and solely Apache. I don't need a full LAMP server. I'm going to be hosting a plain text HTML website. I searched for how to set up Apache but all i find is full LAMP server install guides.. Can someone possibly help or point me in the right direction?

I think I know what you want to do: Step by step to learn the detail (Apache) without the others bothering you, is that right?
Here is my suggestion:

1. Install the apache httpd ---> Very easy, here you go
sudo apt-get install apache2
2. Want to tweak your apache2?? You might have to buy a book or
[http://httpd.apache.org/docs/2.0/howto/](http://httpd.apache.org/docs/2.0/howto/)

Scare?? Don't be. If you change your mind and just want manually do the steps and quickly done your works. Here you go:
[http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/)

By the way, I think you need this one.
[http://www.w3schools.com/html/](http://www.w3schools.com/html/)

---

