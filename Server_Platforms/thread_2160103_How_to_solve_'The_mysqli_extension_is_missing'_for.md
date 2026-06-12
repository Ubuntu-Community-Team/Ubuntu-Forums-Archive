---
title: "How to solve 'The mysqli extension is missing' for PHPmyadmin under NGINX?"
date: 2013-07-05
forum: Server Platforms
---

### Post by lenn-art on 2013-07-05
Hi all,

After installing (succesfully, see this tutorial [http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29](http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29)) a LEMP (E is for nginx) on a VPS, i get puzzled with the following. Puzzled? I'm searching the whole f*&&(( day for a solution ](*,). When i run foo.bar/phpmyadmin, i get the following error 

```
The mysqli extension is missing. Please check your PHP configuration. <a href="Documentation.html#faqmysql" target="documentation"><img class="icon" src="./themes/pmahomme/img/b_help.png" width="11" height="11" alt="Documentation" title="Documentation" /></a>

```

Off course, i googled and tried several solutions like
use the correct php.ini ;-), restarted several times PHP and Nginx
uncommented *mysqli.allow_local_infile = On* in php.ini
added manually to php.ini *extension_dir = ".:/usr/lib/php5/20090626"* (the folder with the .so-files)
added manually to php.ini *extension=/usr/lib/php5/20090626/mysql.so*
added manually to php.ini *extension=/usr/lib/php5/20090626/mysqli.so*

How can i solve this? I can't find anything in the logs; is there a way to view the tail of *all* logs at the same time?

Specs
Ubuntu 12.04 LTS 64bit
NGINGX 
Php5 with FPM
Phpmyadmin

---

### Post by Habitual on 2013-07-05
php -m | grep -i mysqli

perhaps you should spend some more quality time reading some of the 26 comments posted at [http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29](http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29)
there's several responses with the same issue as yours "The mysqli extension is missing"...

---

### Post by lenn-art on 2013-07-06
> **Habitual said:**
> php -m | grep -i mysqli

perhaps you should spend some more quality time reading some of the 26 comments posted at [http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29](http://www.maketecheasier.com/install-lemp-server-in-ubuntu/2012/05/29)
there's several responses with the same issue as yours "The mysqli extension is missing"...
Thanks so far and yes, as you can see, i mentioned the responses in my post .. ;-)

---

