---
title: "how to enable name virtual host?"
date: 2011-11-20
forum: Server Platforms
---

### Post by capt_nemo777 on 2011-11-20
i went to this and edited it
```
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-vhosts.conf
```

to add these

```

<VirtualHost *:80>
	ServerAdmin webmaster@dummyhost.com
	DocumentRoot "/var/www/test"
	ServerName test
        ServerAlias test test.com
	ErrorLog "/var/log/apache2/test-error_log"
	CustomLog "/var/log/apache2/durog-access_log" common
</VirtualHost>

```

then i went to
```
 /etc/hosts 
```
and add this
127.0.0.1   test

i restarted my apache via #  /etc/init.d/apache2 restart

when i go to 

```

http://test

```
it is still pointed to the the index.php a the 
/var/www/index.php ..and not with /var/www/test/index.php

why?

---

### Post by Doug S on 2011-11-20
The httpd-vhosts.conf file is just a provided example in the documentation folder.
Try to edit /etc/apache2/sites-available/default instead.
I suggest that you save the original /etc/apache2/sites-available/default file somewhere as default.original first.
Hope this helps.

---

### Post by capt_nemo777 on 2011-11-20
thanks buddy.it got solved with this [http://brucewampler.wordpress.com/2009/02/28/adding-virtual-hosts-to-ubuntu-apache/](http://brucewampler.wordpress.com/2009/02/28/adding-virtual-hosts-to-ubuntu-apache/)

---

