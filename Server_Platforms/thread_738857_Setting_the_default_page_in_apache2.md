---
title: "Setting the default page in apache2"
date: 2008-03-29
forum: Server Platforms
---

### Post by mkotzev on 2008-03-29
While I realize there are already a bunch of threads about this, none seem to solve my problems.

I'm running Ubuntu 7.10 with an Apache 2.2 installation, PHP5, and mySQL. The apache installation is modularized which seems to make configuration pretty confusing. I need to change the default pages apache looks for in a directory but I can't seem to find the right configuration file or directive that does the trick. Usually I find it inside [FONT="Courier New"]/etc/apache2/httpd.conf[/FONT] but in this particular installation my httpd.conf is blank. I suppose the other options to look in are apache2.conf and [FONT="Courier New"]/etc/apache2/sites-available/default[/FONT] but again to no avail. Anyone know where this directive should be and what it looks like?

~Miro

---

### Post by Poleh on 2008-03-29
you should be able to simply add this directive to the /etc/apache2/sites-available/default file (or any other vhost configuration file)

DirectoryIndex index.html index.php mydefaultpage.html

Apache will then look for a file named in this list, in this order.

Don't forget to reload your apache config after changin it
sudo /etc/init.d/apache2 reload

Hope this helps!

---

