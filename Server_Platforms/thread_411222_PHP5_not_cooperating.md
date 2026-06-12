---
title: "PHP5 not cooperating?"
date: 2007-04-16
forum: Server Platforms
---

### Post by Mathiasdm on 2007-04-16
I'm trying to run a simple script on my computer (I have php5 and apache2 installed), but I keep getting the following error: "Fatal error: Call to undefined function imagecreatefromjpeg() in /var/www/start.php on line 114"

I'm still quite new to all of this, and I'm not sure why I'm getting this error.

---

### Post by nautilus on 2007-04-16
well, that's just php stating that it doesn't know what that function is.

poking my head into the matter quickly, i see that imagecreatefromjpeg is in the GD module of PHP, and those are provided by either:

php4-gd - GD module for php4
php5-gd - GD module for php5

now, once installed, they must be manually enabled:

sudo gedit /etc/php5/apache2/php.ini

or, for php4:

sudo gedit /etc/php4/apache2/php.ini

(scroll down to extensions, maybe around lines 550-560)

add:

```
extension=gd.so
```

or, if it's already there but with a ";" in front of it, delete the ";".

save, restart apache, and reload the page.

---

