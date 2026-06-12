---
title: "WordPress - unable to upload file"
date: 2013-03-02
forum: Server Platforms
---

### Post by satimis on 2013-03-02
Hi all,

localhost install on a VM(guest)

Host - Ubuntu12.04 desktop 64bit
VM(guest) - Ubuntu12.04 desktop 64bit
VirtualBox, Oracle.
WP 3.5.1

Upload file warning:
Error aaa.flv 
aaa.flv exceeds the maximum upload size for this site.

Maximum upload file size: 8MB.

The video file size=12M

Performed following steps without result;

1)
Apache2
$ sudo gedit /etc/php5/apache2/php.ini
change;
upload_max_filesize = 2M
to;
upload_max_filesize = 50M

$ sudo service apache2 restart
 * Restarting web server apache2
 ... waiting    ...done.


2)
Created a php.ini file on /home/satimis/www/wordpress/wp-admin/php.ini
memory_limit = 32M
upload_max_filesize = 32M
post_max_size = 32M
file_uploads = On

$ sudo chmod +x /home/satimis/www/wordpress/wp-admin/php.ini 

Reboot VM


I have tried more than 3 hours without a solution.  Please help.  Thanks

B.R.
satimis

---

### Post by lisati on 2013-03-02
Does your uploads directory (usually /path/to/installation/wp-content/uploads) have write permission?

---

### Post by satimis on 2013-03-02
> **lisati said:**
> Does your uploads directory (usually /path/to/installation/wp-content/uploads) have write permission?
Hi,

$ ls -al /home/satimis/www/wordpress/wp-admin/php.ini ```

-rwxr-xr-x 1 root root 83 Mar  2 17:07 /home/satimis/www/wordpress/wp-admin/php.ini

```
Do I need changing;
Permission   777
Owner  satimis:satimis
?

Thanks

satimis

---

### Post by lisati on 2013-03-02
The PHP.INI file doesn't need write permission to be set (non-writable is probably safer), but the directory /home/satimis/www/wordpress/wp-content/uploads will - this was probably checked during installation.

---

### Post by satimis on 2013-03-02
> **lisati said:**
> The PHP.INI file doesn't need write permission to be set (non-writable is probably safer), but the directory /home/satimis/www/wordpress/wp-content/uploads will - this was probably checked during installation.
Hi,

$ ls -ald www/wordpress/wp-content/```

drwxr-xr-x 6 www-data www-data 4096 Mar  2 15:38 www/wordpress/wp-content/

```

$ ls -ald www/wordpress/wp-content/uploads```

drwxr-xr-x 3 www-data www-data 4096 Mar  2 15:38 www/wordpress/wp-content/uploads

```

ls -al www/wordpress/wp-content/uploads```

total 12
drwxr-xr-x 3 www-data www-data 4096 Mar  2 15:38 .
drwxr-xr-x 6 www-data www-data 4096 Mar  2 15:38 ..
drwxr-xr-x 3 www-data www-data 4096 Mar  2 15:38 2013

```

I suspect whether it is relating permission or owner?   There are many similar threads on Internet relating to this upload problem.  I tried many suggestions but without luck.  I read other folkers were also suffering similar problem.

Performed following steps:-

$ sudo gedit /home/satimis/www/wordpress/phpinfo.php
put following line on the file;
<?php phpinfo() ?>

save and exit.

$ ls -al /home/satimis/www/wordpress/phpinfo.php```

-rw-r--r-- 1 root root 19 Mar 2 21:14 /home/satimis/www/wordpress/phpinfo.php

```

On browser;
[http://localhost/wordpress/phpinfo.php](http://localhost/wordpress/phpinfo.php)

Following line is there
Loaded Configuration File /etc/php5/apache2/php.ini
(Screenshot_01.png)

upload_max_filesize 50M
(Screenshot+02_max_filesize.png)

$ sudo ln -s /etc/php5/apache2/php.ini php.ini

$ sudo chown -R www-data:www-data www/wordpress/wp-admin/php.ini 

Also without solution

satimis

---

### Post by Doug S on 2013-03-02
Isn't this a bit of key feedback (from the OP):> Maximum upload file size: 8MB.
Perhaps, I don't know for sure, this line in /etc/php/apache2/php.ini matters:```
post_max_size = 8M
```

---

### Post by satimis on 2013-03-02
> **Doug S said:**
> Isn't this a bit of key feedback (from the OP):Perhaps, I don't know for sure, this line in /etc/php/apache2/php.ini matters:```
post_max_size = 8M
```
Hi,

Lot of thanks for your advice.

After changing;
post_max_size = 8M

to;
post_max_size = 50M

ran;
$ sudo service apache2 restart

My problem is now solved.  You save me lot of effort

Regards
satimis

---

