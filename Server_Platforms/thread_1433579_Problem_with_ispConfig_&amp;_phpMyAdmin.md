---
title: "Problem with ispConfig &amp; phpMyAdmin"
date: 2010-03-19
forum: Server Platforms
---

### Post by finnj6 on 2010-03-19
Hi when I try to log into phpMyAdmin on my ubuntu box I get the error


Warning: Unknown: open_basedir restriction in effect. File(/usr/share/phpmyadmin/index.php) is not within the allowed path(s): (/var/www/clients/client1/web1/web:/var/www/clients/client1/web1/tmp:/usr/share/php5) in Unknown on line 0

Warning: Unknown: failed to open stream: Operation not permitted in Unknown on line 0

Fatal error: Unknown: Failed opening required '/usr/share/phpmyadmin/index.php' (include_path='.') in Unknown on line 0

I'm trying to open phpMyAdmin in FF using [http://192.168.0.14/phpmyadmin/](http://192.168.0.14/phpmyadmin/)

Can any one help me?

---

### Post by Ryan Dwyer on 2010-03-19
You need to add that include path to your open_basedir directive in /etc/php5/apache2/php.ini. Or just remove it altogether, because safe mode is being removed in PHP6.

---

### Post by finnj6 on 2010-03-19
Hi

Thanks for the quick reply, I've had a look at that file and open_basedir is commented out so the line reads 

```
;open_basedir= 
```

so from what your saying that is correct?

---

### Post by i.r.id10t on 2010-03-19
or install the phpmyadmin package for ispconfig and access it at [https://yourhost:81/phpmyadmin](https://yourhost:81/phpmyadmin)

---

### Post by finnj6 on 2010-03-19
Ok I got it working turned out I was accessing it wrong through my browser. I was using [http://myserver/phpmyadmin](http://myserver/phpmyadmin) where I needed [http://myserver:8080/phpmyadmin](http://myserver:8080/phpmyadmin)

---

