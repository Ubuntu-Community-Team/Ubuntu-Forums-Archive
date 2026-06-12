---
title: "Some folders on web server giving 500 error"
date: 2012-07-26
forum: Server Platforms
---

### Post by Maheriano on 2012-07-26
I installed Apache2 on my Ubuntu Server and if I go to 192.xxx.xxx.xxx/development everything works great. If I go to any other folder like /staging it gives the following error:
> Server error
The website encountered an error while retrieving [http://192.xxx.xxx.xxx/staging/](http://192.xxx.xxx.xxx/staging/). It may be down for maintenance or configured incorrectly.
Here are some suggestions:
Reload this web page later.
HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfil the request.
Originally I had all the files in the main / directory but moved them all under the /development directory so I could have the other 2 (staging and production) in there with it. The 2 new ones I added for some reason don't work.

I've tried restarting Apache successfully multiple times, that didn't fix it. Each folder has the exact same index.php file in them. Any ideas?

---

### Post by spjackson on 2012-07-26
> **Maheriano said:**
> HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfil the request.

When you get this, look in the apache error log (probably /var/log/apache2/error.log).

---

### Post by Maheriano on 2012-07-26
> [Thu Jul 26 15:59:34 2012] [error] [client 192.168.0.121] PHP Warning:  include(../inc/cache.inc): failed to open stream: No such file or directory in /var/www/quotes/index.php on line 2, referer: [http://quotes.domain.com/](http://quotes.domain.com/)
[Thu Jul 26 15:59:34 2012] [error] [client 192.168.0.121] PHP Warning:  include(): Failed opening '../inc/cache.inc' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/quotes/index.php on line 2, referer: [http://quotes.domain.com/](http://quotes.domain.com/)
[Thu Jul 26 15:59:34 2012] [error] [client 192.168.0.121] PHP Warning:  require(includes/config/config.inc.php): failed to open stream: Permission denied in /var/www/quotes/index.php on line 3, referer: [http://quotes.domain.com/](http://quotes.domain.com/)
[Thu Jul 26 15:59:34 2012] [error] [client 192.168.0.121] PHP Fatal error:  require(): Failed opening required 'includes/config/config.inc.php' (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/quotes/index.php on line 3, referer: [http://quotes.domain.com/](http://quotes.domain.com/)...

---

### Post by spjackson on 2012-07-27
You have warnings because /var/www/quotes/index.php does 
```
include(../inc/cache.inc)
```
but /var/www/inc/cache.inc does not exist.

You have error 500 because /var/www/quotes/index.php does
```
require(includes/config/config.inc.php)
```

but the apache user (probably www-data) does not have permission to read /var/www/quotes/includes/config/config.inc.php

---

### Post by Maheriano on 2012-07-27
It was the permissions on the includes folder, I changed it and all the subdirectories to 755. That worked.

---

