---
title: "php and gd problem!"
date: 2005-04-13
forum: Server Platforms
---

### Post by CrustyDOD on 2005-04-13
Hey

I tried 1 script today and figured out that gd thingy is really not working :)

error: Fatal error: Call to undefined function: imagecreatefromjpeg()..

PHP was compile manually:
'./configure' '--prefix=/usr/local/php4' '--with-apxs2=/usr/local/apache2/bin/apxs' '--with-libxml-dir=/usr/local/lib' '--with-zlib' '--with-zlib-dir=/usr/local/lib' '--with-mysql=/usr/local/mysql' '--with-mysqli=/usr/local/mysql/bin/mysql_config' '**--with-gd**' '--enable-sockets' '--enable-mbstring' '--enable-calendar' '--enable-trans-sid' '--enable-exif'

with phpinfo(); i get this about gd:

GD Support 	enabled
GD Version 	bundled (2.0.28 compatible)
GIF Read Support 	enabled
GIF Create Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled
XBM Support 	enabled

i installed GD module for PHP: sudo apt-get install php4-gd

did a few restarts of apache and yet i still get that error..

I'm completly lost here!

What could be wrong, am i missing something?
Do i have to manually compile GD library? or php module? where to get it?

---

### Post by dataw0lf on 2005-04-13
I believe you have to also enable jpeg support.  Ala --with-jpeg-dir.

---

### Post by CrustyDOD on 2005-04-13
So i have to recompile whole PHP with that --with-jpeg-dir=??
OK, what dir?

---

### Post by dataw0lf on 2005-04-13
/usr/lib probably.  Whereever your libjpeg is at.

---

### Post by freddirkse on 2006-10-13
I had php5-gd installed and couldn't get it working properly either.  I had to uncomment this line in my php.ini file:

extension=gd.so

And now all is right with the world.

---

