---
title: "Informing PHP of Pear installation"
date: 2014-10-08
forum: Server Platforms
---

### Post by cov on 2014-10-08
I have a Joomla instalation in which one of the modules apparently needs **Pear**.

My **include_path** variable is:

```
dave@Threepwood:/var/www$ php -c /path/to/php.ini -r 'echo get_include_path()."\n";'
.:/usr/share/php:/usr/share/pear
```

I have located the actual location:

```
dave@Threepwood:/var/www$ pear config-get php_dir
/usr/share/php
dave@Threepwood:/var/www$ ls /usr/share/php/
Archive  data  OS    PEAR5.php    PEAR.php     Structures  XML
Console  doc   PEAR  pearcmd.php  peclcmd.php  System.php
```

The **System.php** file is apparently the file that the **include_path** needs to point to, right?

I'm getting this error in my Joomla front end:

> Fatal error: require_once(): Failed opening required '/var/www/kickstart/libraries/joomla/html/html/content.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/kickstart/modules/mod_roknewspager/lib/helper.php on line 19

---

### Post by cov on 2014-10-08
Oops.

I see the required library is "/var/www/kickstart/libraries/joomla/html/html/content.php", not Pear.

Been barking up the wrong tree, I think.

:oops:

---

