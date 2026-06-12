---
title: "Problem with php after update"
date: 2010-03-19
forum: Server Platforms
---

### Post by jersak on 2010-03-19
Hi there,
Today i made an update using Webmin, and after that php stopped working, instead of running the files it launches a download.

So i checked what was going on, and php module was disabled in apache config. When trying to enable it, it said the file "/usr/lib/apache2/modules/libphp5.so" did not exist, and indeed it disapeared. I tried to reinstal php and apache (with and without --purge, through apt) and it didn't solved the problem. Also i tried copying the file from another machine, also without success (this time it shows " Apache is running a threaded MPM, but your PHP Module is not compiled to be threadsafe.  You need to recompile PHP.") Dont know what to do now, im kinda desperated here because this machine hosts my website =P

---

### Post by lisati on 2010-03-19
I had a similar problem the other day: one of the few PHP web pages I have on my site was launching as a download insted of displaying the page.

The solution I used, based on some information at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), was to purge the PHP modules, reinstall them, and clear the cache in my browser.

---

### Post by jersak on 2010-03-19
Solved it removing both Php and Apache and the installing LAMP.
Not a proper solution i guess but was the only thing crossing my mind.

---

