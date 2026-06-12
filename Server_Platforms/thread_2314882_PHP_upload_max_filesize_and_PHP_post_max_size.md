---
title: "PHP upload_max_filesize and PHP post_max_size"
date: 2016-02-24
forum: Server Platforms
---

### Post by anonymouschief on 2016-02-24
On an Ubuntu 14.04 server, several Apache/PHP5 web applications that I have been installing, say, Zurmo, and SuiteCRM, are stating that my PHP upload and post size values are insufficient. I have them set correctly in /etc/php5/apache2/php.ini. 

[TABLE="class: checked-services, width: 0"]
[TR]
[TD]PHP upload_max_filesize value is: 2M minimum requirement is: 20M[/TD]
[TD][CENTER][COLOR=#CC0000]FAIL[/COLOR][/CENTER]
[/TD]
[/TR]
[TR]
[TD]PHP post_max_size setting is: 8M minimum requirement is: 20M[/TD]
[TD][CENTER][COLOR=#CC0000]FAIL[/COLOR][/CENTER]
[/TD]
[/TR]
[/TABLE]
I have done a grep and cannot find a conf file with the said 2M and 8M values:
```
/etc/php5/fpm/php.ini:upload_max_filesize = 40M/etc/php5/apache2/php.ini.save:upload_max_filesize = 40M
/etc/php5/apache2/php.ini.bak2.recycle:upload_max_filesize = 40M
/etc/php5/apache2/php.ini.save.2:upload_max_filesize = 40M
/etc/php5/apache2/php.ini:upload_max_filesize = 40M
/etc/php5/apache2/php.ini.ucf-dist:upload_max_filesize = 40M
/etc/php5/cli/php.ini:upload_max_filesize = 40M

```

Please help,
AC :popcorn:

---

### Post by SeijiSensei on 2016-02-24
I'll ask the obvious question first:  did you restart Apache after changing the filesize parameter?

Create a file called info.php in the website root with this content:
```
<?php phpinfo() ?>
```
If you view that file with a browser, what do you see for the filesize limit?

---

### Post by anonymouschief on 2016-02-24
Yes, I restarted Apache2.

Here is the snippet from my php.ini file:
```

; Maximum allowed size for uploaded files.
; http://php.net/upload-max-filesize
upload_max_filesize = 40M

```

```

; Maximum size of POST data that PHP will accept.
; http://php.net/post-max-size
post_max_size = 40M

```

PHP Info file:
[TABLE="width: 600"]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]upload_max_filesize[/TD]
[TD="class: v, bgcolor: #CCCCCC"]2M[/TD]
[TD="class: v, bgcolor: #CCCCCC"]2M[/TD]
[/TR]
[/TABLE]

[TABLE="width: 600"]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]post_max_size[/TD]
[TD="class: v, bgcolor: #CCCCCC"]8M[/TD]
[TD="class: v, bgcolor: #CCCCCC"]8M[/TD]
[/TR]
[/TABLE]


Where are these values being taken from?

---

### Post by Habitual on 2016-02-24
look for more than one php.ini
```
find / -name php.ini -type f
```

---

### Post by anonymouschief on 2016-02-24
I have searched. There are just these, and they have all been updated (see my first post):
```

/etc/php5/fpm/php.ini
/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini

```

---

### Post by Habitual on 2016-02-24
Sorry about that. :)

---

### Post by anonymouschief on 2016-02-24
I have Googled this for ages; all to no avail. I get several confirmations that /etc/ph5/apache2/php.ini is the only configuration file that is i effect. I have no idea where the 2M and 8M values are being derived from. I know that we do not need to restart Linux to apply config changes. However, I will do that right now. I am sure that nothing will change.

[TABLE="width: 600"]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Configuration File (php.ini) Path[/TD]
[TD="class: v, bgcolor: #CCCCCC"]/etc/php5/apache2[/TD]
[/TR]
[TR]
[TD="class: e, bgcolor: #CCCCFF"]Loaded Configuration File[/TD]
[TD="class: v, bgcolor: #CCCCCC"]/etc/php5/apache2/php.ini[/TD]
[/TR]
[/TABLE]
Please help, Linux gurus.

---

### Post by anonymouschief on 2016-02-24
I have solved this, more or less as a workaround. There is nothing wrong with the php.ini file, however, this webapp is either not reading php.ini or is overriding the values in php.ini. I found a workaround at [http://www.maheshchari.com/increase-php-file-upload-limit/](http://www.maheshchari.com/increase-php-file-upload-limit/) and used .htaccess to apply the values that I needed, that is:

```

php_value upload_max_filesize 40M
php_value post_max_size 60M
php_value memory_limit 768M

```

---

