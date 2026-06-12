---
title: "PHP question: Zend memory manager"
date: 2007-07-20
forum: Server Platforms
---

### Post by Macuyiko on 2007-07-20
The last couple of days I've been running into a few PHP problems. I've asked around on various forums and the PHP IRC channel but so far I've had no luck. So I'll try here, without going into too much details :).

Basically, I'm trying to suppress a zend_mm_heap corrupted error, by disabling the Zend Memory Manager.

I've exported USE_ZEND_ALLOC=0 and tried running the scripts in question using PHP-CLI, that disables the Zend Memory Manager (so does phpinfo(); tell me). So now I want to go through Apache (I'm using mod-php, not php-cgi), so I add the following to apache2.conf: SetEnv USE_ZEND_ALLOC 0.

However, after reloading, the Memory Manager is still enabled! The environment var is there though.

So is there a way to disable it? Or does it only work when using PHP-CLI?

Thanks in advance.

---

