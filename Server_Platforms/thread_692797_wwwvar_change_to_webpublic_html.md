---
title: "/www/var change to /web/public_html?"
date: 2008-02-10
forum: Server Platforms
---

### Post by erosion on 2008-02-10
hello,
I install ubuntu server and the default web root is /var/www .
I made new directories "web" and "public_html. 
I edited the config' file to tell the server this, but on restart the server says that the directories do not exist. 
But the directories do exist?
the code is correct.
what am i doing wrong?
anyone got any clues?:mad:

---

### Post by mzembe on 2008-02-10
Make sure the new directories have the same permissions as the old location.

---

### Post by mzembe on 2008-02-10
Just for fun I installed apache & changed the root by issuing a 
mv www web
Edited /etc/apache2/sites-available/default values for DocumentRoot & one other instance of '/var/www' in the same configuration file, and issued a 
/etc/init.d/apache2 restart

The localhost site loaded, failed (purposefully, I tried before restarting), and loaded again.

Maybe you didn't see the other instance in the configuration file? /var/web & /var/web/apache2-default should be mode 755, everything in apache2-default mode 644 from the installation defaults.

---

