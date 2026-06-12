---
title: "PhpMyAdmin - Trying to weed out possible bug"
date: 2006-09-05
forum: Server Platforms
---

### Post by jetthe on 2006-09-05
Hi,

after I installed Ubuntu Server (LAMP) a few days a go I proceeded to install PhpMyAdmin from the repos.
However I noticed that the symlink from /etc/apache2/conf.d/phpmyadmin.conf to /etc/phpmyadmin/apache.conf was not set up. Everything else in the postinst-file of the package however ran correctly. There is some security crucial stuff in apache.conf (as protecting the config-directories) so it should really be set up correctly.

So, before I file this as a bug, have anyone else experienced the same thing?  (easily checked by performing an "ls -l" in your "/etc/apache2/conf.d"-directory to see if there exists a symlink "phpmyadmin.conf -> /etc/phpmyadmin/apache.conf" or not).

Greetings.

---

