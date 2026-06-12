---
title: "Strange issue with php5."
date: 2013-11-21
forum: Server Platforms
---

### Post by klabacita on 2013-11-21
Hi my friends.

I had a funny issue with ubuntu server lts, 12.0.x and php53+apache.

U know that some times is easy to test our php scripts under the CLI:

> 
php script.php


I had server same model for test than my production server, same version, but the funny thing is this one, If a go to apache DocumentRoot and test my script, desn't run:

> 
cd /var/www
php script.php


Won't do nothing.

But if I leave the dir and run the script using the absoluth path works:

> 
cd ..
php /var/www/script.php


I had try to figure out the issue but don't get why this behaviour, apache logs won't show nothing wrong, any tips I will appreciated.

x64 server updated!!!

---

### Post by spjackson on 2013-11-23
> **klabacita said:**
> 
```

cd /var/www
php script.php

```
Won't do nothing.

What do you get with this?
```

cd /var/www
php -v
which php
echo $PATH

```
If that doesn't help, it might possibly be to do with the content of script.php.

You won't get anything in the apache logs because php cli has nothing to do with apache.

---

