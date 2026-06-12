---
title: "Down grading php"
date: 2010-05-30
forum: Server Platforms
---

### Post by captsisko on 2010-05-30
it's as the title says.

My remote server is running on php 5.3.*

but I need php 5.2.*. Can anyone please help and tell me what command line entries
I need to make to get my php to the desired version, please ?

---

### Post by richardjh on 2010-06-01
You will have to uninstall php 5.3 first.

You then can download the [source code for php5.2]("http://uk3.php.net/get/php-5.2.13.tar.bz2/from/a/mirror") and compile it yourself, which for php is usually very straight forward.

Alternatively you could point your apt sources at Karmic and install php from there.
A quick Google found [this link to someone who has successfully done just that]("http://maxmanders.co.uk/web-development/revert-to-php-5-2-in-ubuntu-10-04-lucid-lynx/").

---

