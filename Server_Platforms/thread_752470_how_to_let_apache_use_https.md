---
title: "how to let apache use https?"
date: 2008-04-11
forum: Server Platforms
---

### Post by android6011 on 2008-04-11
I dont know where to start on this. I tried a couple old forum posts but I cant seem to make things work.

---

### Post by tubezninja on 2008-04-11
Have you looked at the "certificates and security" section [on this documentation page?]("https://help.ubuntu.com/7.10/server/C/httpd.html")  I used it, and I was able to get things up and running.

---

### Post by android6011 on 2008-04-11
I did sudo a2enmod ssl

and I get

Can't connect securely because the site uses an older, insecure version of the SSL protocol.

(Error code: ssl_error_ssl2_disabled)

---

### Post by android6011 on 2008-04-14
bump....

---

### Post by jpeddicord on 2008-04-14
You're going to need an SSL certificate. A few providers give out free trials, but many cost $50-$300 per year. You could also self-generate one, but that will cause a whole bunch of security warnings to pop up in the browser about unverified sites and whatnot.

Once you have that, you need to configure your SSL certificate:
[http://www.debian-administration.org/articles/349](http://www.debian-administration.org/articles/349)

The meat of it is at the bottom of that page where you put the details into your VirtualHost file.

---

### Post by android6011 on 2008-04-14
ok thanks for the greate reply, but i have apache2 installed and I get:

-bash: apache2-ssl-certificate: command not found

---

