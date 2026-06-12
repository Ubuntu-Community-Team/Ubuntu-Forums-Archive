---
title: "Apache - index.html is served instead of index.php"
date: 2010-12-27
forum: Server Platforms
---

### Post by adit on 2010-12-27
In the directory /var/www I have 2 files:
1) index.html
2) index.php
When I type [http://localhost](http://localhost) in firefox location bar, I get index.html.  I want Apache to serve index.php.  How to do that?

---

### Post by HugoSerrano on 2010-12-27
humm... You may need libapache2-mod-php5 to enable that.
test it with [http://localhost/index.php](http://localhost/index.php)

If that works, you can add

DirectoryIndex index.php

in the file /etc/apache2/sites-enable/000-default
under the <Directory /var/www/>

ex:
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                DirectoryIndex index.php
                Order allow,deny
                allow from all
        </Directory>

---

### Post by adit on 2010-12-27
My php installation is OK.  The link _[http://localhost/index.php](http://localhost/index.php)_ works.
I added the line DirectoryIndex index.php
in the file /etc/apache2/sites-enabled/000-default
under the <Directory /var/www/>
I restarted apache.  Still it sends to the browser only index.html not index.php.

---

### Post by adit on 2010-12-27
It works after rebooting entire operating system.  Why it happens like this?  Should I reboot ubuntu each time I edit any configuration file?

---

### Post by HugoSerrano on 2010-12-27
rename or move the index.html

---

### Post by foltor on 2012-02-28
Thank solved my problem

---

### Post by godzalli44 on 2012-10-20
> **HugoSerrano said:**
> humm... You may need libapache2-mod-php5 to enable that.
test it with [http://localhost/index.php](http://localhost/index.php)

If that works, you can add

DirectoryIndex index.php

in the file /etc/apache2/sites-enable/000-default
under the <Directory /var/www/>

ex:
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                DirectoryIndex index.php
                Order allow,deny
                allow from all
        </Directory>

wow thanx!!!. it works.

add DirectoryIndex index.php to <Directory /var/www/>
and "service apache2 restart"

---

