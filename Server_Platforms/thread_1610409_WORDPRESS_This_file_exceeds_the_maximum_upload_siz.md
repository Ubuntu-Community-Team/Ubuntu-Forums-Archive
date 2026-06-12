---
title: "WORDPRESS This file exceeds the maximum upload size for this site."
date: 2010-10-31
forum: Server Platforms
---

### Post by mrebanza on 2010-10-31
So yea here is the fix . . . for the notoriously annoying . . . WORDPRESS This file exceeds the maximum upload size for this site.

EDIT THIS FILE change upload_max_filesize to something big than 2M (really a 2M default wtf?) . . . I am going with 64M because I love BIG FILES . . . . 

ect/php5/apache2/php.ini

```

; Maximum allowed size for uploaded files.
upload_max_filesize = 64M
```

After that You will need to restart Apache2 web server by banging either of these into a terminal . . .


```

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
or
sudo /etc/init.d/apache2 restart
```

I accually alway use stop then start . . . idk why


hope this helps some Googlers / Ubuntu"ers" . . . Enjoy.

---

### Post by tazosmr on 2013-04-26
this might help- **add this in .htacess:**

```

<IfModule mod_php5.c>
php_value post_max_size           40M
php_value upload_max_filesize     40M
php_value memory_limit            500M
</IfModule>

```

---

### Post by wildmanne39 on 2013-04-27
Thread closed. Please do not post in old threads.

---

