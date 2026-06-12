---
title: "Ubuntu LAMP and MediaWiki"
date: 2006-12-14
forum: Server Platforms
---

### Post by TopDog on 2006-12-14
I have a server at work with Ubuntu LAMP 6.06. I've installed MediaWiki through Apt.

I can now access MediaWiki through [http://localhost/mediawiki/](http://localhost/mediawiki/)

But I want to change the path to simply [http://localhost/](http://localhost/) or in worst case [http://localhost/somethingelse/](http://localhost/somethingelse/)

Anyone know where this is configured? And where is the MediaWiki files located? They are not under /var/www/mediawiki as they would be if I'd installed it manually...

---

### Post by marianom on 2006-12-14
Regarding changing the url, see:
[http://meta.wikimedia.org/wiki/Eliminating_index.php_from_the_url](http://meta.wikimedia.org/wiki/Eliminating_index.php_from_the_url)
and
[http://meta.wikimedia.org/wiki/Using_a_very_short_URL](http://meta.wikimedia.org/wiki/Using_a_very_short_URL)

I don't know where mediwiki files are when you install it from the repos. Anyway, run 

```
slocate LocalSettings.php
```

This is one of the most important files in mediawiki, if you find it, you'll find the rest.

---

### Post by az on 2006-12-14
> **TopDog said:**
> I have a server at work with Ubuntu LAMP 6.06. I've installed MediaWiki through Apt.

I can now access MediaWiki through [http://localhost/mediawiki/](http://localhost/mediawiki/)

But I want to change the path to simply [http://localhost/](http://localhost/) or in worst case [http://localhost/somethingelse/](http://localhost/somethingelse/)

Anyone know where this is configured? And where is the MediaWiki files located? They are not under /var/www/mediawiki as they would be if I'd installed it manually...

/etc/apache2/sites-available

change the redirectmatch in apache-default to /var/www

---

### Post by az on 2006-12-14
> **azz said:**
> /etc/apache2/sites-available

change the redirectmatch in apache-default to /var/www

Whoops!  That should be /var/www/mediawiki so that anything that acesses /var/www (DocumentRoot) goes there.

---

### Post by TopDog on 2006-12-14
Thanks for great responses!

---

