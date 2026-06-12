---
title: "Apache2 ~ Help"
date: 2006-10-12
forum: Server Platforms
---

### Post by zingyGecko on 2006-10-12
I installed Ubuntu 6.06 Server edition with the LAMP option and now I want to set it up so that when I go to [http://hostname/](http://hostname/) it'll bring me to the pages that are in /var/www, and if I go to [http://hostname/~username](http://hostname/~username), it'll bring me to ~username/www. Does anyone know how to do this?

---

### Post by seuaniu on 2006-10-12
[http://httpd.apache.org/docs/2.0/howto/public_html.html]("http://httpd.apache.org/docs/2.0/howto/public_html.html")is the place to start looking.  Generally, if a user has a 'www' dir in their $HOME with the right permissions, then apache2 will pick it up at [http://server.com/~username](http://server.com/~username).  I can't remember what the permissions are off the top of my head, but they should be in the link.

---

