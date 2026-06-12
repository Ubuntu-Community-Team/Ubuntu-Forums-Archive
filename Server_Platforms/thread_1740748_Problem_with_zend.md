---
title: "Problem with zend ???"
date: 2011-04-27
forum: Server Platforms
---

### Post by lazkom on 2011-04-27
Hello,

I have problem with installation of zend
show me this error

# php -v
Failed loading /usr/local/Zend/lib/php-5.3.x/ZendGuardLoader.so:  /usr/local/Zend/lib/php-5.3.x/ZendGuardLoader.so: wrong ELF class: ELFCLASS64

my php version is :

PHP 5.3.3-1ubuntu9.3 with Suhosin-Patch (cli) (built: Jan 12 2011 16:08:14)
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2010 Zend Technologies


I use i686 platform and apache - Server version: Apache/2.2.16 (Ubuntu)

Ideas ?


Thanks,
Lazar.

---

### Post by falko on 2011-04-27
It seems as if you installed the version for x86_64 instead of for i686...

---

### Post by lazkom on 2011-04-28
I Installed this 
Zend Guard Loader (Runtime for PHP 5.3)	5.5.0 (64 bit)
from zend site!

but not working.

any ideas ?

---

### Post by falko on 2011-04-28
You must install the version for 32bit, not 64bit.

---

### Post by lazkom on 2011-04-28
Okay,
i installed 32 bit version

but new error is :


# php -v
PHP Fatal error:  [Zend Guard Loader] Extension "Zend Guard Loader" cannot be loaded twice in Unknown on line 0


Zend Guard Loader (Runtime for PHP 5.3)	5.5.0 (32 bit)	

ZendGuardLoader-php-5.3-linux-glibc23-i386.tar.gz from Zend WS :)

Any ideas ?

Thanks to advanced :)

---

### Post by lazkom on 2011-05-02
Any ideas how i solve my problem ?

---

