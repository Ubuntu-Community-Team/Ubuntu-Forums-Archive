---
title: "php running as root"
date: 2016-05-08
forum: Security
---

### Post by clearski on 2016-05-08
Hi, everyone.  

My public server runs nginx/1.4.6 & PHP 5.5.9-1 atop of Ubuntu 14.04.4. 

 I hardened my PHP and eventually came to test the configuration with *SektionEins's PHP Secure Configuration Checker* ([https://github.com/sektioneins/pcc](https://github.com/sektioneins/pcc))  

Everything looks fine, except (!) it says I have a critical risk: **"Got root? Test for root access on non-windows systems     you are root! Executing PHP as root is hardly ever necessary."**

Here are the PHP processes:  

```
root      5705  0.0  2.7 228016 13944 ?        Ss   11:05   0:00 php-fpm: master process (/etc/php5/fpm/php-fpm.conf)
www-data  5708  0.0  0.9 228016  4552 ?        S    11:05   0:00 php-fpm: pool www 
www-data  5709  0.0  1.5 228168  7796 ?        S    11:05   0:00 php-fpm: pool www
```

  I also used spawn-fcgi to launch php as user www-data, set the /var/run/ socket to www-data,  still I got the same message.

Any ideas about what's wrong?

---

### Post by SeijiSensei on 2016-05-08
I use Apache, but the idea is the same.  There is a "stub" program that runs as root.  It spawns child processes running with www-data as the owner.  People connecting to the server talk to these unprivileged listeners; they don't touch the root stub.

Processes that bind to ports < 1024 require root privileges so there's no way you can bind the program to port 80 or 443 as user www-data.  That's why the method I described was created.

---

### Post by clearski on 2016-05-11
I am sorry for the late answer.

So, should I disregard this warning and consider that there's no need to worry?

---

### Post by SeijiSensei on 2016-05-12
Yes.  As far as I know, PHP never runs as root on any mainstream Linux distro.  It has the same permissions as the www-data user.

---

### Post by clearski on 2016-05-19
Thank you!!!

---

