---
title: "Migrating from RHE4 Dapper Dapper Drake LAMP"
date: 2006-08-13
forum: Server Platforms
---

### Post by Cyberflunky on 2006-08-13
I have switch one of my web servers over to Dapper from RHE4. The Apache configuration is much different setup is much different. I have not been able to find the source of one error that is listed below. I get it trying to make a [visual-captcha]("http://www.ejeliot.com/pages/2") work. Can anyone point me in the right direction.


Warning: imageftbbox() [function.imageftbbox]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 296

Warning: imagefttext() [function.imagefttext]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 304

Warning: imageftbbox() [function.imageftbbox]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 296

Warning: imagefttext() [function.imagefttext]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 304

Warning: imageftbbox() [function.imageftbbox]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 296

Warning: imagefttext() [function.imagefttext]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 304

Warning: imageftbbox() [function.imageftbbox]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 296

Warning: imagefttext() [function.imagefttext]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 304

Warning: imageftbbox() [function.imageftbbox]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 296

Warning: imagefttext() [function.imagefttext]: Could not find/open font in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 304

Warning: Cannot modify header information - headers already sent by (output started at /var/www/wowdirectory.com/html/php-captcha.inc.php:296) in /var/www/wowdirectory.com/html/php-captcha.inc.php on line 320
&#65533;&#65533;&#65533;&#65533;

---

### Post by mr_niceguy on 2008-02-13
[https://help.ubuntu.com/community/PhpPear#head-193387e746a12003d885219dc4a0170720de8a39](https://help.ubuntu.com/community/PhpPear#head-193387e746a12003d885219dc4a0170720de8a39)

---

