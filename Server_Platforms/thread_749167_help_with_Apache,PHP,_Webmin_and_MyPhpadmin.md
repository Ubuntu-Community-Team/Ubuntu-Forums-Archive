---
title: "help with Apache,PHP, Webmin and MyPhpadmin"
date: 2008-04-08
forum: Server Platforms
---

### Post by ianb72 on 2008-04-08
I have installed Dapper LAMP server and webmin and configured webmin as the guide on [LAMP for NOOBS]("http://www.cjfay.com/lamp.html")

I am having the same problem as wilshire in his message[ PHP problem]("http://ubuntuforums.org/showthread.php?t=698790")

When I access my server from a proxy or anyone else accesses it all they get is the index of / and apache2-default/ (see screenshot)

I know I should have my index.php in the /var/www folder but even when I have done that I get an error and all I am putting in the index.php page is this:
[PHP] <html>
<head>
<title> PHP Test Script </title>
</head>
<body>
<?php
phpinfo( );
?>
</body>
</html>[/PHP]

when in Terminal I typed : sudo a2enmod php5
 and it told me that this module is already enabled
But when I try opening the index.php file in firefox all it does is ask me to save it or download it

Following the other mail from wilshire and looking at the /etc/apache2/apache2.conf file the 2 lines about php look like this:
[HTML] #AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps[/HTML]
Should I remove the # from the beginning of them?

I would also Like to install MyPHPAdmin, how do I go about this and how do I get it running, as I installed it on before and could not get it to run so I did a clean install of the LAMP server, do I install it from Synaptics or direct from the myphpadmin website?

My IP Address is 79.73.164.238 if anyone wants to look what happens when they to get my index.php page as I have left the index page in /ver/www folder

If anyone can help I would be extremely grateful

Many thanks
Ian

---

### Post by insineratehymn on 2008-04-08
Are you sure that index.php has execution permissions?

```
chmod ugo+x index.php
```

---

### Post by jrib on 2008-04-08
follow the trouble shooting steps at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and tell us the results/errors you receive

---

### Post by ianb72 on 2008-04-08
I was just looking else where and it said about permissions to the index.php file.

Do I have to do that with all the php files I put on the server or just the index file??

Many thanks
Ian

---

### Post by insineratehymn on 2008-04-08
All PHP files must have executable permissions.

Just get all of them together and type:
```
 chmod 755 *.php
```

---

