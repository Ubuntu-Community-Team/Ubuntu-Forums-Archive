---
title: "Lamp Server with Oracle Support"
date: 2007-11-30
forum: Server Platforms
---

### Post by AnhD on 2007-11-30
Hi All,
     I know the LAMP server is mostly for MySQL & PHP but most companies will have other tools that may be of MS or Oracle's products.  What would it take to make the PHP of the LAMP server compiled with Oracle support?  Or it is already is?  I would like my PHP application to be able to access remote Oracle databases.

Thanks,
Doug

---

### Post by koenn on 2007-11-30
Oracle supports php, and the offer "Zend Core" for download - I'd assume its 'oracle-compatible' then.
check their website:
[http://www.oracle.com/technology/tech/php/zendcore/index.html](http://www.oracle.com/technology/tech/php/zendcore/index.html)

---

### Post by AnhD on 2007-11-30
I am hoping that the ubuntu lamp package will compile PHP with Oracle support in place.  All I have to do is download and install the Oracle Instant Client with a few configuration and we are set.  I could recompile PHP, but that would messed the update of the lamp package and most bridges from PHP to other sources, such as MySQL, Python, etc.  I would like to be able to use apt-get update/upgrade and still have the lamp package updated with security and enhancements patches.


Thanks,
Doug

---

