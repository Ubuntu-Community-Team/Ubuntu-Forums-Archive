---
title: "Help me ditch apache for ngnix"
date: 2010-09-06
forum: Server Platforms
---

### Post by waloshin on 2010-09-06
So if I disable apache 2 my ngnix server will serve the files in /var/www automatically.

---

### Post by BkkBonanza on 2010-09-06
I've used nginx for a couple years. It's great. But you still have to configure where you want to get files from and other options. The config format is pretty nice though. I like it better.

Anyway, if you have specific questions I can help out. It's a great lightweight web server and is used by some of the biggest sites on the web. 

Also now #3 in popularity after Apache and MS IIS according to Netcraft's monthly survey.

You can install nginx and test it by serving your files on an alternate port like 8080, until you know that it works fine with your files. The only thing that is likely to cause issues is if you use "rewrite rules" and special modules in Apache.

The config for PHP is also fairly different because it uses fastcgi.

---

