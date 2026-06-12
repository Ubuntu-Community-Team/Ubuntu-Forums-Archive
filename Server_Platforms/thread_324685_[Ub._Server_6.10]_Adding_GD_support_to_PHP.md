---
title: "[Ub. Server 6.10] Adding GD support to PHP"
date: 2006-12-24
forum: Server Platforms
---

### Post by supr on 2006-12-24
Hi!

what's the easiest way to add support gor GD (freetype) to my freshly installed LAMP configuration?

Thanks!
supr

---

### Post by ehowell on 2007-01-31
I know this thread is old but since it came up on google at like #5 I thought I would still answer it (since I had the same question and just found the answer).

Run:

sudo apt-get install php5-gd

Then restart apache

sudo /etc/init.d/apache2 restart

---

### Post by outofnicks on 2007-03-16
I, also, had the same question and just found my answer if you wanted to stay with PHP4 and Apache 1.3.x for some reason (I do).

I didn't want to run Apache2 or PHP5, because I wanted to emulate on my localhost the server config of my www sites. I found php-gd in the package manager, it took only a few seconds to install then after restarting Apache there was GD support listed in phpinfo.php. There's a few other php4 modules there, also for php5.

---

