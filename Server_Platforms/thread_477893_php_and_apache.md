---
title: "php and apache"
date: 2007-06-18
forum: Server Platforms
---

### Post by Quickjelly on 2007-06-18
I'm running a LAMP server with apache2 and php5. My intention is to run torrentflux on the server.

Now I've installed all the following packages: 
torrentflux 2.1.7
libapache2-mod-php5 5.1.2
php5 5.1.2
php5-common
php5-mysql
php5-mysqli
apache2
apache2-common
apache2-mpm-prefork
apache2-utils
mysql-server
mysql-client

However, when I point firefox to "localhost/torrentflux" on the server (or ipadress/torrentflux from some other computer) the browser prompts me to download a PHTML file or choose an application to open it. This is of course not what I want to do, I want to runt the php scripts, not download them.

So I searched around a bit and I've tried som things suggested for this problem but nothing seems to work.

Also, I activated the php5 module with apache with this command:

```
a2enmod php5
```

It tells me that the module has been enabled, so why isn't it working?

Thanks for any help.

---

### Post by Mr. C. on 2007-06-19
In one of your httpd conf files, you should see a line simiar to:

```
  AddType application/x-httpd-php .php
```

Add the .phtml extension and reload apache:

```
 AddType application/x-httpd-php .php .phtml
```

MrC

---

### Post by Quickjelly on 2007-06-19
That line was missing alltogether, so I added it and now it works fine.

Thanks :)

---

### Post by Mr. C. on 2007-06-19
Excellent!

---

### Post by crxvfr on 2007-06-19
I need to do this as well but I'm a noob and don't know what directory the file is in. Are there several?

---

### Post by Mr. C. on 2007-06-19
Learn to use locate:

locate httpd.conf

MrC

---

