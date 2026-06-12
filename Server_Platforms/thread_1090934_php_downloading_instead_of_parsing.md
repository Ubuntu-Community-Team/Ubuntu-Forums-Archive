---
title: "php downloading instead of parsing"
date: 2009-03-08
forum: Server Platforms
---

### Post by davidself1001 on 2009-03-08
I am a newbie so be patient.  I have a test.php file in /var/www and when I try to bring up that page with localhost/test.php it thinks it's a file go be downlaoded instead of parsing the PHP commands in the test.php file.  I have searched thru and followed the LAMP setup guide including the troubleshooter recommendation about this problem related to verifying that the libapache2-mod-php5 is properly loaded and still get the same results.  I originally installed apache2 and php5 individually then did the LAMP installation with  sudo tasksel install lamp-server.  Any help would be appreciated.

---

### Post by hictio on 2009-03-09
On top of my head... Have you checked that the Apache config file includes:

```

AddType application/x-httpd-php .php

```

---

### Post by davidryder on 2009-03-09
Restart apache and clear your browser cache... if that doesn't work go to command line and try

```
php -a
phpinfo();

```

Post any errors (if you receive any).

---

### Post by davidself1001 on 2009-03-09
Applied the AddType line to httpd.conf.  Did the php -a, phpinfo(); with no errors.  At least none stated as an error per se.   A friend mentioned that I needed a cgi-bin dir for my .php files to execute from but I haven't done that nor do I know how or where to do it.   Anybody got any apache books (or torrents) that you would recommend to get me past the complete dumb-*** stage?

---

### Post by davidryder on 2009-03-09
Just to be clear, you cleared your browser cache right?

---

### Post by mrsteveman1 on 2009-03-10
CGI bins are for executing scripts outside the apache process, with PHP we typically execute it with mod_php so it doesn't need a CGI dir.

Just make sure you have the right type setup like an above post mentioned, and make sure php5 itself is actually installed along with libapache2-mod-php5

---

### Post by buzzmandt on 2009-03-13
> **hictio said:**
> On top of my head... Have you checked that the Apache config file includes:

```

AddType application/x-httpd-php .php

```

can you let those of use that are really stupid in on where this config file is and what it's name is please.  I'm having the same problem of php wanting to download instead of parse.  thanks

found it after some more digging it is in /etc/apache2/apache2.conf
added the line above and restarted apache with  /etc/init.d/apache2 restart
and all is well now.   thanks

---

### Post by hyper_ch on 2009-03-14
rather use:

```

sudo a2enmod php5

```

instead of manually adding the addtype.

---

