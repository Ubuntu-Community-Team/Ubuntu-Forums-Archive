---
title: "Menalto Gallery2 Install Help on Ubuntu 9.10"
date: 2010-01-11
forum: Server Platforms
---

### Post by 3L33T on 2010-01-11
HELP!  Is there anyone out there running Menalto's Gallery2 on Ubuntu 9.10?

I'm trying to install Menalto Gallery2 2.3.1 on Ubuntu 9.10 + php 5.3.1 + apache 2.2.12 + postgresql 

php5 is configured and running correctly.  I verified the config using gallery2 ghcc (gallery host compatibility checker) and running a "test.php" (<?php phpinfo();?>).  a2enmod php5 is enabled.

Whenever I try to run the install script in the [http://mysite.com/gallery2/install](http://mysite.com/gallery2/install) folder, the "index.php" file is not executing :(   ...it just downloads the "index.php".

What am I missing?

---

### Post by 3L33T on 2010-01-11
OK, it worked this time.  The problem was the browser I was using for some reason is not running the index.php file.

I used firefox 3.5.7 this time and now the install is loading.

Now during database setup, I got an error that says "You must have the PostgreSQL PHP module installed".  Hmmmmm....

---

### Post by 3L33T on 2010-01-11
...i'm replying to my own posts...WEIRD.

The problem this time was "php5-pgsql".  All I needed is to install it :D

---

### Post by 3L33T on 2010-01-11
ITS DONE!!  INSTALLED! and working :D

---

