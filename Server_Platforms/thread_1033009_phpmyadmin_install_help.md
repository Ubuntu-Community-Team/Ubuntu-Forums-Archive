---
title: "phpmyadmin install help"
date: 2009-01-06
forum: Server Platforms
---

### Post by jdcnosse on 2009-01-06
I have Ubuntu 8.04 LTS server edition, so no GUI, and I've tried installing phpmyadmin before and I noticed it installs into a directory in the /etc/phpymyadmin folder.

The only problem is that I have my www folder set as /home/james/www.

So when I go to my site via a different computer on my network (since my server has no GUI and I run it headless) I can't get to the phpmyadmin page.

How do I get it setup correctly to be in my www folder?

---

### Post by q.dinar on 2009-01-07
if you install it from repository it is symlinked to /var/www or aliased to /phpmyadmin location. so you can open it with "http://ipofyourcomputer/phpmyadmin". if you document root is not /var/www try to symlink phpmyadmin or alias it to proper place. it is not in /etc/ itself, there are only configuration files. find/see where from it is symlinked and symlink from that place to your place or make alias in a apache's configuration file: in phpmyadmin's file which is in /etc/apache2/conf.d or in other file.

---

