---
title: "PHP won't run code"
date: 2008-05-06
forum: Server Platforms
---

### Post by dienbien001 on 2008-05-06
My old server with Gutsy worked fine. I've just upgrade tu Hardy, and have an error.
I create a file test.php:
```
<?php 
phpinfo(); 
?>
```

But the output is the same with the source code.
PHP didn't do its job. But I don't know how to solve this problem
I installed libapache2-mod-php5, reloaded apache2, installed PHP5, Apache2, enabled mod php5 for apache2.
I tried this link: [http://ubuntuforums.org/showthread.php?t=471730](http://ubuntuforums.org/showthread.php?t=471730)
but it didn't work.

I've just installed phpmyadmin, and it work perfect.
I don't know why my test.php didn't work?

SOLVED: OK, now it works perfect :D, i just edit the file /etc/apache2/mods-enabled/php5.conf: remove all # at line Addtype that I commented before.

---

