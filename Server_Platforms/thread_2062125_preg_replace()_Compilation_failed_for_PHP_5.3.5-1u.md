---
title: "preg_replace(): Compilation failed: for PHP 5.3.5-1ubuntu7"
date: 2012-09-24
forum: Server Platforms
---

### Post by resting on 2012-09-24
I'm getting this error after i did an apt-get install php5-gd.
Think it might had upgraded the php5 version too.

Warning (2): preg_replace(): Compilation failed: unknown option bit(s) set at offset 0 [CORE/Cake/Utility/Inflector.php, line 545]

How do I resolve it?

Ubuntu
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

---

### Post by xdracco on 2012-09-24
Did you update CakePHP too? Odds are, CakePHP needs updating too.

---

### Post by resting on 2012-09-24
> **xdracco said:**
> Did you update CakePHP too? Odds are, CakePHP needs updating too.

Hm...odd...somehow the PCRE version was upgraded today to 8.12 2011-01-15 from 7.8 2008-09-05.

Could be because I did apt-get install libpcre3 but didn't reboot the server.

Anyway, the error message is now gone with the new PCRE.

Thanks :)

---

### Post by xdracco on 2012-09-25
Odd. You shouldn't have had to reboot the server just for libpcre.. but glad it worked itself out.

you should mark thread as solved. =D

---

