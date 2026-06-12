---
title: "PHP, unable to load dynamic library ps.so"
date: 2008-07-08
forum: Server Platforms
---

### Post by michellez on 2008-07-08
PHP Warning:  PHP Startup: Unable to load dynamic library
'/usr/lib/php5/20060613+lfs/ps.so' - /usr/lib/php5/20060613+lfs/ps.so: cannot open
shared object file: No such file or directory in Unknown on line 0

I did have the popular (it seems) Imagick problem which I fixed after searching the forums. This happened after upgrading Ubuntu. Not having so much luck on the new error though.

Thanks,
Shell

---

### Post by windependence on 2008-07-08
Does /usr/lib/php5/20060613+lfs/ps.so actually exist on your machine?

-Tim

---

### Post by michellez on 2008-07-08
No it isn't.

/usr/lib/php5/20060613+lfs/ps.so: No such file or directory

What is "PS"?

Thank you,
Shell

---

### Post by windependence on 2008-07-08
I think this is postscript.

Try this:

```
sudo apt-get install pslib
```


-Tim

---

### Post by michellez on 2008-07-08
I have done apt-get install pslib-dev and apt-get install pslib1.

The file does still not exist and I still get the same error.

Thanks,
Shell

---

### Post by michellez on 2008-07-08
I've realised (I think..) this needs a similar fix to Imagick (duh!) using:

> pecl install ps

It doesn't work though! :(

> ...
configure: creating ./config.status
config.status: creating config.h
running: make
/bin/sh /var/tmp/pear-build-root/ps-1.3.6/libtool --mode=compile gcc  -I. -I/tmp/pear/cache/ps-1.3.6 -DPHP_ATOM_INC -I/var/tmp/pear-build-root/ps-1.3.6/include -I/var/tmp/pear-build-root/ps-1.3.6/main -I/tmp/pear/cache/ps-1.3.6 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/cache/ps-1.3.6/ps.c -o ps.lo
mkdir .libs
 gcc -I. -I/tmp/pear/cache/ps-1.3.6 -DPHP_ATOM_INC -I/var/tmp/pear-build-root/ps-1.3.6/include -I/var/tmp/pear-build-root/ps-1.3.6/main -I/tmp/pear/cache/ps-1.3.6 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/cache/ps-1.3.6/ps.c  -fPIC -DPIC -o .libs/ps.o
/tmp/pear/cache/ps-1.3.6/ps.c:37:16: error: gd.h: No such file or directory
/tmp/pear/cache/ps-1.3.6/ps.c: In function âzif_ps_open_memory_imageâ:
/tmp/pear/cache/ps-1.3.6/ps.c:1337: error: âgdImagePtrâ undeclared (first use in this function)
/tmp/pear/cache/ps-1.3.6/ps.c:1337: error: (Each undeclared identifier is reported only once
/tmp/pear/cache/ps-1.3.6/ps.c:1337: error: for each function it appears in.)
/tmp/pear/cache/ps-1.3.6/ps.c:1337: error: expected â;â before âimâ
/tmp/pear/cache/ps-1.3.6/ps.c:1350: error: âimâ undeclared (first use in this function)
/tmp/pear/cache/ps-1.3.6/ps.c:1350: error: expected â;â before âzend_fetch_resourceâ
make: *** [ps.lo] Error 1
ERROR: `make' failed

Huh o_O

Thanks,
Shell

---

### Post by michellez on 2008-07-08
Sorted!

> 
sudo apt-get install libgd2-xpm-dev
sudo pecl install ps


Now working error free :)

Annoying all this "messed up" after a dist upgrade..

Thanks,
Shell

---

### Post by speedymedia on 2008-07-29
Ok...When I run this:

sudo pecl install ps 

It asks:

5 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
 1. path to pslib installation? : 

1-1, 'all', 'abort', or Enter to continue: 

---------------

I've tried /usr/lib,  /usr/local/lib,
I've tried searching the drive for pslib and pointing it there...but no dice.  

What am I doing wrong?

---

### Post by rabatitat on 2008-08-07
you have to get the dependecies for pslib:
libpng and libjpeg

after which you'll be able to run pecl install ps without hitches.

just get the whole graphics library package as michellez stated:

libgd2-xpm-dev

So the installation process would be:

sudo apt-get the following:

build-essential (for building debian packages - useful for any developer)
php5-dev (module development)
libgd2-xpm-dev (graphics dependecies of libsp1)
libsp1 (PostScript library)

run:

sudo pecl install ps

(when it prompts you for the path of pslib, just press enter)

add to php.ini:
extension=ps.so

restart your web server:
sudo /etc/init.d/apache2 restart

You can test it out by running a php script on your browser with the following line:
$p = ps_new();

No errors either means it running well or you've turned off error reporting on your php server (LOL).

Hope this helps. :D

---

