---
title: "PHP file download problem - have read other answers"
date: 2009-09-08
forum: Server Platforms
---

### Post by aberends on 2009-09-08
I have installed Apache 2.2.13 and PHP5 on my computer (running Jaunty Jackalope netbook remix), and after two weeks of attempts cannot get the browser to stop prompting for a download of files with a .php extension.  I have tried the following (restarting Apache and clearing browser cache after each one);

remove/purge and reinstall libapache2-mod-php
edit httpd.conf to include AddType text/html .php
edit httpd.conf to include AddHandler php-script .php .html
edit httpd.conf to include AddType application/x-httpd-php .php .html .htm

I have also tried all possible combinations of the above three configuration options. I am not sure what to do at this point as that seems to be the limit of the advice I have found in the documentation and elsewhere.  Please help!

---

### Post by Cardale on 2009-09-08
Is a complete re-install not an option? Of Ubuntu I mean.  Would probably save a lot of time.

---

### Post by aberends on 2009-09-10
I can reinstall, just trying to not have to do that.

---

### Post by recentcoin on 2009-09-10
Did you install mod_php?

---

### Post by aberends on 2009-09-17
is that different from libapache2_mod_php?

---

