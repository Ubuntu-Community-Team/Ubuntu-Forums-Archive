---
title: "Running mod_php &amp; fastcgi/php-fpm parallel on ubuntu"
date: 2013-02-17
forum: Server Platforms
---

### Post by ronaldv on 2013-02-17
Hi,

I was hoping to test-drive php-fpm on my apache server parallel to mod_php (e.g. 1 virtual host running mod_php and another running php-fpm); on ubuntu that is.

But I found out that fastcgi/phpfpm requires apache2-mpm-worker while mod_php requires apache2-mpm-prefork and that these two exclude each other.

So is it really true that on one ubuntu server you can not have php-fpm & mod_php run in parallel?

Any done this before?

---

