---
title: "How to make adminer work"
date: 2017-03-05
forum: Ubuntu/Debian BASED
---

### Post by austin-green on 2017-03-05
OS is Trisquel, an Ubuntu derivative; browser is IceCat, a FireFox derivative. Installed adminer package, but browsing to [http://localhost/adminer/](http://localhost/adminer/) gives
```
 IceCat can't establish a connection to the server at localhost.
```
After some web research, have added symlinks in /etc/apache2/conf-available and /etc/apache2/sites-available to /etc/adminer/apache.conf. Can anyone give me some hints as to where to look next?

---

### Post by brucehohl on 2017-03-06
Last year I installed adminer for a project on Ubuntu 14.04-64 LTS server.  My notes which follow may help:

1+ INSTALL sqlite apache2 php5 
   Test connection to web server.

2+ ADMINER install:
   $ cd /var/www/html
   $ sudo wget [https://www.adminer.org/static/download/4.2.2/adminer-4.2.2-en.php](https://www.adminer.org/static/download/4.2.2/adminer-4.2.2-en.php)

   $ sudo mkdir /var/www/html/data  # put sqlite db’s here
   $ ln -s /var/www/html/adminer-4.2.2-en.php /var/www/html/data/index.php

   Create /var/www/html/data/test0.db.  (SQLite db)
   [http://localhost:80/data](http://localhost:80/data)  # open to adminer program as user www-data
   To create a new DB www-data must have write permission to the directory.
   To edit a DB www-data must have write permission to the directory & file.
   To protect a DB file or directory do not grant these permissions to www-data.

   Good general overview including how to install plug-ins.
   [https://www.adminer.org/static/screencast/srigi.mp4](https://www.adminer.org/static/screencast/srigi.mp4)
   
   Option:
   Admin Editor = db portal designed for users versus admins.
   [https://www.adminer.org/static/download/4.2.2/editor-4.2.2-en.php](https://www.adminer.org/static/download/4.2.2/editor-4.2.2-en.php)

---

### Post by austin-green on 2017-03-07
Many thanks for replying. Your hints enabled me to fix the problem! :)

Basically, I fell at the first hurdle:
> **brucehohl said:**
> 
1+ INSTALL sqlite apache2 php5 
   Test connection to web server.

I browsed to 'localhost' to test Apache2 and it failed. I found that browsing to 'myhostname' worked, and after rooting around in the Apache2 config files, found that I had changed ports.conf a long time ago, to listen explicitly on 'myhostname:80' only; I forget now why I did it. Duuhh... :rolleyes::redface:

Adding a line 'Listen localhost:80' did the trick, and now adminer works fine.

---

