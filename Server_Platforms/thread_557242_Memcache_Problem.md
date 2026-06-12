---
title: "Memcache Problem"
date: 2007-09-22
forum: Server Platforms
---

### Post by mantomin on 2007-09-22
Hello!
I have installed memcache (libraries + daemon) in my Ubuntu 7.04, and I couldn’t use it with the php-CLI when I’m not the root user. 

```

mantomin@laptop:/var/www/test$ php5 memcache.php 

Fatal error: Class 'Memcache' not found in /var/www/test/memcache.php on line 3

mantomin@laptop:/var/www/test$ sudo php5 memcache.php
Server's version: 1.2.2<br/>
Store data in the cache (data will expire in 10 seconds)<br/>
Data from the cache:<br/>
object(stdClass)#3 (2) {
  ["str_attr"]=>
  string(4) "test"
  ["int_attr"]=>
  int(123)
}

```

When I’m mantomin user php shows me the Class not found error. However if I execute the script with sudo or root user all is ok.

I think that’s permissions problem but… what file/directory I should give permissions???

Thanks a lot!

---

