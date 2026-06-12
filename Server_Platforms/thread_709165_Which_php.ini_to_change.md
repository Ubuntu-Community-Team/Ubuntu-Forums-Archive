---
title: "Which php.ini to change?"
date: 2008-02-27
forum: Server Platforms
---

### Post by kramer65 on 2008-02-27
Hello,

I use ubuntu but this question is about the centOS server which I use at my webhost. Since this is my favourite forum I thought I would ask here..

I need to set allow_url_include to on. I SSH into the server and ran the command 
find / -name php.ini

It returns the following:
find: /proc/29307: No such file or directory
/usr/lib/php.ini
/usr/local/lib/php.ini
/usr/local/Zend/etc/php.ini
/usr/local/cpanel/3rdparty/etc/php.ini
/scripts/php.ini

Which php.ini do I need to change? Why are there more than one actually?

---

### Post by azadpanchi on 2008-02-27
It is most probably /usr/local/Zend/etc/php.ini

To be sure do this, SSH into the server and run 'php -v | less'

Fairly close to the top you will find out with php.ini is being called on, run your regular trusty test php script and find out if changes are visible.  Additionally I think in WHM now there is an option under Service Configurations for PHP Configurations, see if you can make the change there because if you recompile apache through easy apache or cpanel your changes will go bye bye.

---

### Post by Mr. C. on 2008-02-27
If you have multiple PHP installations, the location of the default php.ini file may be configured differently for each.

Some of those php.ini files (eg. the one in cPanel is a template)

Running **php -v** is fine - but you have to know *which* php is running via command line (which is based on PATH), and which is running under, say, apache.

Locate all your php binaries and php apache modules (eg. mod_php5.so) to verify what is installed.  Use the nice little phpinfo() function in a php web page to help sort it out:

```
<html>
<head>
<title>PHP Info</title>
</head>
<body>
<?php

// Show all information, defaults to INFO_ALL
phpinfo();

// Show just the module information.
// phpinfo(8) yields identical results.
//phpinfo(INFO_MODULES);

?>
</body>
</html>
```

MrC

---

