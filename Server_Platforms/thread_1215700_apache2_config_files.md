---
title: "apache2 config files?"
date: 2009-07-17
forum: Server Platforms
---

### Post by rsmseys on 2009-07-17
I've installed apache2, but it appears as though some files are missing such as httpd.conf and certain modules like mod_rewrite. What could I do to install all of these again properly?

---

### Post by ibutho on 2009-07-17
The config files are in /etc/apache2. To enable or disable apache 2 modules, use a2enmod and a2dismod.

---

### Post by rsmseys on 2009-07-17
Is the httpd.conf file supposed to be blank? Mine is. :S

---

### Post by jonobr on 2009-07-17
default will be empty, your looking for /etc/apache/apache2/apache2.conf

---

### Post by cpetercarter on 2009-07-17
There will also be individual configuration files for each of your enabled sites in /etc/apache2/sites-enabled.

You can enable a module with the a2enmod command (eg a2enmode rewrite), but dont forget to restart Apache afterwards for the change to take effect.

---

