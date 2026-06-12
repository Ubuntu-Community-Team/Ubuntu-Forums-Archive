---
title: "Apache2 and zoneminder"
date: 2014-09-22
forum: Server Platforms
---

### Post by stuoolong on 2014-09-22
Hi, I hope someone can point me in the right direction. I'm a server n00b.

My intention is to run zoneminder on ubuntu server 14.04. I am having trouble getting apache2 to run zoneminder. I have verified that both services are running, and when I go to my localhost I can see the apache2 "it's working!" splash.

The help guides for zoneminder say that you need to create a symlink for zoneminder's apache.conf file in the apache2/conf.d directory. However I have the newer version of apache2 that has the conf-available/conf-enabled structure. I understand the process of symlinking to the conf-available directory and using a2enconf, which I have done, but I'm missing something in getting zoneminder to run on the server, or in making it visible.

Hope someone can help. Thanks in advance.

---

### Post by nerdtron on 2014-09-22
Just passing by....

> ubuntu server 14.04

Have you verified the correct document root? In 14.04 the default root for apache should be on /var/www/hmtl

---

### Post by stuoolong on 2014-09-22
Thanks for passing by! Yes, I am seeing the file /var/www/html/index.html.

Edit - I solved the problem, it's a little embarassing actually...I neglected to write /zm after the localhost IP address in my browser....  :p
Thanks all.

---

