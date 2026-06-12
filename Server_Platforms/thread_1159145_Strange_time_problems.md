---
title: "Strange time problems"
date: 2009-05-14
forum: Server Platforms
---

### Post by _Oleg_ on 2009-05-14
Hi all.

well i am newby, so sorry if its stupid question, just point me to a right topic.

----
Problem.

I am writing (via php) files to cache but suddenly , its start to write a wrong dated files. no idea whats wrong...

few examples

console date - Thu May 14 18:37:40 EEST 2009
php date - 2009-05-14 18:38:00

file_put_contents('foo.bar',1);
date("H:i:s", filemtime('foo.bar'))

>> 2009-05-14 18:38:00
BUT!

console >> ls -la

-rw-r--r-- 1 webserver webserver   60 May 14 18:38 foo.bar
-rw-r--r-- 1 webserver webserver  314 May 14 17:38 write.php

here is a trick
write.php was modified a second ago, after that runned via url and createa file at one hour more.


via winscp it looks like 
foo.bar     60    14.05.2009 19.38.00
writer.php  314   14.05.2009 18.38.00


--------------------
Can anybody tell what wrong with it? 

i have problem , my cache crates, but filemtime return me a wrong date (one hour difference always).....

---

### Post by mbeach on 2009-05-14
my first quess would be that php has a timezone issue.  I believe there is a timezone setting in your php.ini file, but if this is a hosted machine, your provider may give you another way of setting the php time.

quick reference:
[http://www.electrictoolbox.com/correct-php-timezone/](http://www.electrictoolbox.com/correct-php-timezone/)

---

