---
title: "HTTP help as all vhosts redirecting to default site"
date: 2013-02-13
forum: Server Platforms
---

### Post by xkaliburx on 2013-02-13
I have a server running only nagios, but going to run a few smaller sites on the box.  I setup a vhost, setup the servername, etc. but when I hit that vhost, HTML pages work and come up, but when I hit a PHP page it thows a 301 and sends me to the nagios site on that box.

/etc/apache2/conf.d has a nagios.conf with a few rewrite rules, but the thing I noticed, it's only on php files. If I goto [www.newsite.com/test.html](www.newsite.com/test.html) I get my test page (in that vhost), yet if I goto [www.newsite.com/index.php](www.newsite.com/index.php), I get the 301 and moved to nagios.

I'm sure it's something simple I am not seeing, but any help is appreciated as I already cut DNS over figuring these are easy things!

Tnx.

---

### Post by SeijiSensei on 2013-02-14
Did you read the sections on web hosting in the [Server Guide](https://help.ubuntu.com/12.04/serverguide/)?

---

