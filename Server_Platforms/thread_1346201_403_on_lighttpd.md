---
title: "403 on lighttpd"
date: 2009-12-04
forum: Server Platforms
---

### Post by shiggydiggy on 2009-12-04
OS: Karmic
Hey guys, I've installed lighttpd, php5 and mysql to do some dev but whenever I go to my phpinfo file (127.0.0.1/phpinfo.php, physical location /var/www/) it comes up as a 403 forbidden. It's chmod to 10777 so i don't know what the issue is. The two "it works" html files that come with it work fine

---

### Post by madverb on 2009-12-04
Do any .php files work?
You need to enable php loading in lighttp

---

### Post by shiggydiggy on 2009-12-04
I thought I did. any up to date guides around?

---

### Post by madverb on 2009-12-04
I've never done it in lighttp but in apache you just need mod_php and enable in the apache conf or .htaccess.

There should be plenty of guides around on how to do it.

---

### Post by shiggydiggy on 2009-12-04
Ok, I've done it. /etc/lighttpd/conf-available/10-fastcgi.conf needed to be moved to /etc/lighttpd/conf-enabled/
pretty straight forward lol but i'm a windoze user so meh.

---

### Post by madverb on 2009-12-04
There's one for the knowledgebase.

---

### Post by ionplay on 2012-04-18
had the same problem on fresh lighttpd on ubuntu 10.04 install

triple checked permissions
and copying fastcgi.conf to enabled directory
etc....

ultimately the modules were not loaded (not sure how or why), but executed the following and it works properly now

sudo lighttpd-enable-mod fastcgi fastcgi-php

hope this helps anyone else landing on this page

---

### Post by lisati on 2012-04-18
Thread closed, necromancy.

---

