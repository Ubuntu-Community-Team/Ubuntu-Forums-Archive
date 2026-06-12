---
title: "Is this a smart idea? Or a disaster waiting to happen?"
date: 2008-08-01
forum: Security
---

### Post by PooingCavy on 2008-08-01
Hi, I am looking to build a webserver and a "vault" server:\. Ive been wondering about combining them, but I worry about security.

Lets say I want to have two seperate hard drives: A spinning "platter" drive, and a SSD. I want to put my websites and related on the normal hard drive, and family photos or home videos on the SSD.

Do you guys think it is possible to make the security so that no one except for the people who physically access the computer can see the sensitive material. I'd like to combine them, but I don't want anything to leak on the internet. There is no 'illegal' stuff on there, but my parents freak out about leaking photos on the internet, and if a goldmine of material gets on there, that will be bad.

---

### Post by daleus on 2008-08-01
If you have a webserver serving directory /var/www (example) why would anyone be able to see /media/ssdcard (example)?

---

### Post by Dr Small on 2008-08-01
If you are on a local network, the server and rest of the computers are there too, you could just open the firewall on the server so everyone can see the pictures, but on the router, don't forward port 80 to your system. By keeping it like this, no one from outside can access your server.

---

### Post by mdsharp24 on 2008-08-01
[http://httpd.apache.org/docs/1.3/howto/htaccess.html](http://httpd.apache.org/docs/1.3/howto/htaccess.html)

---

