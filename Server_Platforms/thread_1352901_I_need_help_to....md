---
title: "I need help to..."
date: 2009-12-12
forum: Server Platforms
---

### Post by welfair on 2009-12-12
Hey thanks for your time I'm trying to set up a server and I have NO idea what I should have on it for services I guess that any web page that could help with this would be good but im so lost i need it to do file storage for all OS types and host a small web site and email I hope that I don't seem to dumb.. 

Thank you,
your friend,
Welfair

---

### Post by gabo.cr on 2009-12-12
Is not dumb, using Ubuntu Server is the smartest thing you can do.
I am working on one myself, (still learning) but it is very cool.
There is a lot of info out there, here is a link:

[https://help.ubuntu.com/9.10/serverguide/C/index.html](https://help.ubuntu.com/9.10/serverguide/C/index.html)

---

### Post by koenn on 2009-12-12
> **welfair said:**
>  I'm trying to set up a server and I have NO idea what I should have on it for services

The services you need mostly depend on what you want that server to do, so maybe you'll have to think about that first.
Meanwhile, the server guide index gabo points to may offer some inspiration.

---

### Post by Cheesemill on 2009-12-12
To set up a web server with apache mysql and php (this is usually everything you need to run any sort of website) just run the command:
```
sudo apt-get install lamp-server^
```
and then put your content in /var/www/

To set up Samba (to share files to Windows machines):
[http://lmgtfy.com/?q=ubuntu+samba](http://lmgtfy.com/?q=ubuntu+samba)

---

### Post by namei on 2009-12-12
The most important thing is what kind of service you need to provide exactly.
File storage for all OS types: FTP service(vsftpd, pureftpd, proftpd), Samba service
Small web site: Apache, Nginx, Lighthttpd
Email: postfix, sendmail...

You can read the manual on their website.

> **welfair said:**
> Hey thanks for your time I'm trying to set up a server and I have NO idea what I should have on it for services I guess that any web page that could help with this would be good but im so lost i need it to do file storage for all OS types and host a small web site and email I hope that I don't seem to dumb.. 

Thank you,
your friend,
Welfair

---

### Post by welfair on 2009-12-12
wow thank you all that was fast I appreciate your help so much 

thank you ,
Welfair

---

