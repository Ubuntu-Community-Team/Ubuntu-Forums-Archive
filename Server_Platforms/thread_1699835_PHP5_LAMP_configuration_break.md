---
title: "PHP5 LAMP configuration break?"
date: 2011-03-04
forum: Server Platforms
---

### Post by jshipps on 2011-03-04
I've recently setup LAMP on my VPS.
I believe I may have broken the PHP configuration somehow, not 100% sure exactly how, but I'm getting internal server errors upon loading .php files.

Any information on a fix for this would be appreciated :)

*Edit* phpmyadmin still runs fine so maybe there's an error in my Apache configuration or my VirtualHosts?

---

### Post by huangsen365 on 2011-03-04
you should check the log

---

### Post by SeijiSensei on 2011-03-05
^This

Usually 'internal server errors' arise when you have a misplaced directive.  Often it's because you have a .htaccess file in a directory with a directive not allowed by the controlling "AllowOverride" directive for that virtual host or directory.

---

### Post by tgalati4 on 2011-03-05
Increase memory limit in /etc/php5/php.ini

---

