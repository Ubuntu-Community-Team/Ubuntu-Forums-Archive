---
title: "finding phpmyadmin"
date: 2009-12-04
forum: Server Platforms
---

### Post by shiggydiggy on 2009-12-04
Hey I'm running lighttpd php5 and mysql successfully on my karmic. I did apt-get install phpmyadmin and it installed, it's all there, but how do i run it? 127.0.0.1/phpmyadmin doesn't work.
what do i have to do?

---

### Post by munky99999 on 2009-12-04
Assuming you aren't using Jaunty or Karmic.

Make sure in this file:
/etc/apache2/apache2.conf

There's a line which says:
Include /etc/phpmyadmin/apache.conf

Reload apache once you do this:
/etc/init.d/apache2 restart

Then goto the website. If you are using Jaunty or Karmic. Do a restart on apache2 anyway. That might fix it up.

---

