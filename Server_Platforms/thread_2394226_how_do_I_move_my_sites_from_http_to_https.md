---
title: "how do I move my sites from http to https ?"
date: 2018-06-14
forum: Server Platforms
---

### Post by marchello_lippi2 on 2018-06-14
Hi all, 
I would like to move my sites from http to https, how do I start (I am using apache2) ?
Thanks ahead for any hint.

---

### Post by SeijiSensei on 2018-06-14
First you'll need to buy an SSL certificate. There's lots of information about this on the web.

---

### Post by walts48 on 2018-06-15
> **marchello_lippi2 said:**
> Hi all, 
I would like to move my sites from http to https, how do I start (I am using apache2) ?
Thanks ahead for any hint.

Use Let's Encrypt?

> Let’s Encrypt is a free, automated, and open certificate authority (CA), run for the public’s benefit.

[URL="https://letsencrypt.org/"]https://letsencrypt.org/

[/URL][URL="https://letsencrypt.org/"]
[/URL]

---

### Post by SeijiSensei on 2018-06-15
I had problems getting Let's Encrypt to work on my CentOS 6 servers so I didn't mention that solution.  There were dependency issues for Certbot on that platform.  (Don't know about Ubuntu.)  I planned to try again soon.  Maybe now is the time?

---

### Post by QIII on 2018-06-15
I use Let's Encrypt on my websites running on Ubuntu servers (I use NGINX rather than Apache, but I don't think that should be an issue) and have certbot renew the certs regularly.

---

