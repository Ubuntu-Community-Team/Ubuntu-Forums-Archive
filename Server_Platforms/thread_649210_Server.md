---
title: "Server"
date: 2007-12-24
forum: Server Platforms
---

### Post by krammer66 on 2007-12-24
I would like to gain some experience by building a server. Where do I start? I am using Feisty.:confused:

---

### Post by eggdeng on 2007-12-24
Depends on what you want to do. If you want to serve a website, start by installing the apache web server 
```
sudo apt-get install apache2
```
Type localhost in the address bar of firefox to check if it is up and running.
Then save your webpages to /var/www. Your homepage should be called index.html or similar. Alternatively you could install the Ubuntu server edition which comes with apache, php & mysql by default, but no GUI.

---

### Post by TurboRush on 2007-12-24
That's somewhat of a broad answer. The easiest thing to set a goal for what you want to do, i.e., I want to create an online photo gallery... 

That way you have a definitive end point for that test and you can build from it as you get more comfortable. 

The purpose of a server could range from everything from a dedicated DNS, to application, to web, mail, to a single physical box that does all of those.

---

### Post by FakeOutdoorsman on 2007-12-24
A good start would be taking a look at the Ubuntu Wiki entry on [Apache, MySQL, and PHP]("https://wiki.ubuntu.com/ApacheMySQLPHP").  It shows more than just how to install what you need.  Also look at [The Perfect Server - Ubuntu Gutsy Gibbon (Ubuntu 7.10)]("http://howtoforge.com/perfect_server_ubuntu7.10") from howtoforge.com, although I think the Ubuntu Wiki page is more useful.

---

### Post by R00t3rMan on 2007-12-25
I would recommend starting with something fairly simple like a file server.

---

