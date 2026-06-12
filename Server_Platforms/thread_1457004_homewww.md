---
title: "/home/*/www"
date: 2010-04-18
forum: Server Platforms
---

### Post by Vegan on 2010-04-18
I used to have Apache setup to be able to show pages from /home/*/www so that a user had a web page

from there I could assign a vanity URL to any of them.

I need to get my Apache2 back up.

---

### Post by Xipher on 2010-04-18
What you're looking for is the UserDir configuration and module.

---

### Post by Vegan on 2010-04-18
Is there any quick way to get somthing in my httpd.conf file?

Its blank right now

---

### Post by Vegan on 2010-04-18
I am using a graunched solution for now

sudo mkdir www
sudo chown nobody:nogroup www/
sudo mkdir www/site1
sudo mkdir www/site1
sudo chmod -R 777 www/

add the solder to SAMBA and I can develop pages ad nauseum. Webmin makes adding a new URL trivial, I just wanted to have Apache2 support /home as well for remote users.

---

