---
title: "php file is blank in browser, help"
date: 2010-05-24
forum: Server Platforms
---

### Post by AresArtemis1 on 2010-05-24
hi, professionals, finally I finished deploying work for my web server with Ubuntu 10 lts, everything testing is pass, only the php file issue, I put a testing php file in the /var/www/testing.php

but I open a firefox, and then I saw a blank page, I am sure that Apache read the file, but why return a blank page in browser, any professional know why, could you please teach me how to solve this small issue

best thanks and regards,

:guitar::guitar::guitar:

I am going to donate my webserver space to Ubuntu team!

---

### Post by new_tolinux on 2010-05-24
> **AresArtemis1 said:**
> I put a testing php file in the /var/www/testing.php
Please post the contents of your testing php-file between [noparse][php] and [/php][/noparse] tags.
Or use this one:
[php]
<?php
phpinfo();
?>
[/php]

---

### Post by Ryan Dwyer on 2010-05-24
Make sure you're accessing the page through [http://localhost](http://localhost) and not file:///. Then make sure you have libapache2-mod-php5 installed.

---

### Post by cdenley on 2010-05-24
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
cat /var/www/testing.php
echo -e "GET /testing.php HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

---

### Post by wojox on 2010-05-24
Post the contents of **testing.php**

---

### Post by AresArtemis1 on 2010-05-24
hi, professionals, the content as follows:

<html>
<head>
  <meta content="text/html; charset=ISO-8859-1"
 http-equiv="Content-Type">
  <title></title>
</head>
<body>

[COLOR=#000000] [COLOR=#0000BB]<?php
phpinfo[/COLOR][COLOR=#007700]();
[/COLOR][COLOR=#0000BB]?>[/COLOR] [/COLOR] 
<br>
</body>
</html>

but still is blank page

---

### Post by cdenley on 2010-05-24
You still haven't posted the output from the commands I gave you, so it is a little difficult to help.

---

### Post by AresArtemis1 on 2010-05-24
I followed the instruction check the following things:


By default, the Apache 2 Web server is configured to run PHP5           scripts. In other words, the PHP5 module is enabled in Apache2           Web server automatically when you install the module. Please           verify if the files           /etc/apache2/mods-enabled/php5.conf  and           /etc/apache2/mods-enabled/php5.load           exist.

they are exist, I saw

---

### Post by cdenley on 2010-05-24
> **AresArtemis1 said:**
> By default, the Apache 2 Web server is configured to run PHP5           scripts. In other words, the PHP5 module is enabled in Apache2           Web server automatically when you install the module. Please           verify if the files           /etc/apache2/mods-enabled/php5.conf  and           /etc/apache2/mods-enabled/php5.load           exist.


Installing apache does not install apache's php5 module. I believe installing the php5 module enables it automatically, but apache is not restarted automatically, and you cannot use newly installed modules until apache2 is restarted. I cannot proceed to help you further until you run the commands I provided and post the output.

---

### Post by ArchCast on 2010-05-24
Just to do some basic troubleshooting here... can you run php from the command line?

```
php /var/www/testing.php
```

---

### Post by cdenley on 2010-05-24
> **ArchCast said:**
> Just to do some basic troubleshooting here... can you run php from the command line?

```
php /var/www/testing.php
```

He would probably have to install the command-line interpreter first.
```

sudo apt-get install php5-cli

```

I still suggest posting the output from these troubleshooting commands I posted earlier.
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart
cat /var/www/testing.php
echo -e "GET /testing.php HTTP/1.0\n"|nc -q 1 127.0.0.1 80

```

---

### Post by ArchCast on 2010-05-24
Also, do you have logging enabled?  If so, what's in your access.log and error.log?

---

### Post by joeyoung25 on 2011-09-09
OK I know this post is old but I am looking for a solution. There was an update for php 2 days ago so I installed them in Webmin and now none of my php code works. Its just blank. It worked before the update. You can see my php info file by going to
support.servitechlabs.com /test.php   Any help would be appreciated. Thanks

---

### Post by SeijiSensei on 2011-09-09
deleted; double post when server fell over

---

### Post by SeijiSensei on 2011-09-09
What do you see in /var/log/apache2/error.log?

---

