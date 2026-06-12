---
title: "How can I force my *.html files through the PHP interpretator?"
date: 2007-06-17
forum: Server Platforms
---

### Post by jingo811 on 2007-06-17
How can I force my *.html files through the PHP interpretator?

I'm trained to install and configure WAMP in a Windows XP environment.  In the Apache2 config file "httpd.conf" there's a line one could add at the bottom of the file.
```
AddType application/x-httpd.php .html
```

In Ubuntus Desktop LAMP setup I went into its equivalent
```
gksudo "gedit /etc/apache2/apache2.conf"
```
and tried to edit the existing line
```
AddType application/x-httpd.php .php
```
into this but I couldn't force my *.html file to be interpretated as an *.php file.
```
AddType application/x-httpd.php .html
```

Has any LAMP admin managed to accomplish this trick that could be done in WAMP.
By the way I installed all the Apache, PHP, MySQL packages  that was released around 2007 May for WAMP if it helps.

---

### Post by jonathan.jbkt on 2007-07-23
I am looking for a solution to this as well.

---

