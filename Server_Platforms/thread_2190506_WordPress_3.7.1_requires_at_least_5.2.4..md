---
title: "WordPress 3.7.1 requires at least 5.2.4."
date: 2013-11-27
forum: Server Platforms
---

### Post by bellalamb on 2013-11-27
running 7.04 server

get this message when trying to run wordpress

"Your server is running PHP version 5.2.1 but WordPress 3.7.1 requires at least 5.2.4."

try

sudo apt-get install php5 

and get message that php is already uptodate

how do I get a later version?

---

### Post by Habitual on 2013-11-27
php -v output please.

---

### Post by bellalamb on 2013-11-27
PHP 5.2.1 (cli) (built: Jul 23 2008 05:57:56)

---

### Post by Iowan on 2013-11-27
I ran into similar problems. Once the version goes past EOL (End of Life), it still works, but adding/updating becomes difficult. I eventually upgraded to a more current version.

---

### Post by bellalamb on 2013-11-27
I am leaning towards that, but so many websites, dreading the transfer!

---

### Post by kenetik on 2013-11-27
> **bellalamb said:**
> I am leaning towards that, but so many websites, dreading the transfer!

Dreading the transfer? Transfer where? Or are you referring to the upgrade? 

PHP Upgrade isn't that difficult, not to mention it is reversible if you experience issues.

Are you using numerous different platforms (cms's) for the numerous websites?

How are you hosting? (VPS? Shared?)

---

### Post by bellalamb on 2013-11-27
Transfer to new operating system/disk

PHP upgrade would be ideal - but how?

using webmin/virtualmin for managing the websites

hosting just with dual adsl connections on one server

---

### Post by kenetik on 2013-11-27
> **bellalamb said:**
> Transfer to new operating system/disk
You don't have to transfer Operating Systems/Disks just to upgrade PHP.

> **bellalamb said:**
> PHP upgrade would be ideal - but how?
What version of Ubuntu and Apache are you running? Are you familiar with command line?

> **bellalamb said:**
> using webmin/virtualmin for managing the websites
Webmin is great and offers running multiple versions of PHP for separate (virtual servers as Webmin refers to it.)

> **bellalamb said:**
> hosting just with dual adsl connections on one server
Haha, is that sufficient, for MULTIPLE websites? Have you considered managed hosting?

---

### Post by bellalamb on 2013-11-28
Ubuntu 7.04 server

Apache 2.2.3

PHP 5.2.1 (Wordpress I am trying to install needs 5.2.4+)

---

### Post by kenetik on 2013-11-28
Bellalamb,

This will get you the latest stable apache and php:
--
[http://askubuntu.com/questions/109404/how-do-i-install-latest-php-in-supported-ubuntu-versions-like-5-4-x-in-ubuntu-1/109544#109544](http://askubuntu.com/questions/109404/how-do-i-install-latest-php-in-supported-ubuntu-versions-like-5-4-x-in-ubuntu-1/109544#109544)

---

### Post by bellalamb on 2013-11-28
thank you, but that doesn't work with Ubuntu 7.04

---

