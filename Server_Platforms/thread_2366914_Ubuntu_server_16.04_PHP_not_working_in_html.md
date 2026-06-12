---
title: "Ubuntu server 16.04 PHP not working in html"
date: 2017-07-23
forum: Server Platforms
---

### Post by patdundee on 2017-07-23
Hi Guys
I have just upgraded from Ubuntu Server 14.04 to Ubuntu Server 16.04 which also upgraded PHP to v7

All php included in html files used to work, however sice the upgrade PHP only works within an html file if it called as an include or require once file. Any php included with the html is not parsing

I have added the following lines to the site conf file

<filesmatch ".(html|htm)$">
SetHandler application/x-httpd-php5
</filesmatch>

Still no joy.

Any help greatly appreciated please

Many thanks

---

### Post by wildmanne39 on 2017-07-23
*Thread moved to **Server Platforms**.*

---

### Post by pqwoerituytrueiwoq on 2017-07-23
you need to install libapache2-mod-php
[https://askubuntu.com/questions/632918/php-showing-source-code-in-localhost/821275#answer-821275](https://askubuntu.com/questions/632918/php-showing-source-code-in-localhost/821275#answer-821275)

---

### Post by patdundee on 2017-07-23
Hi
Already have that installed :(

---

### Post by lisati on 2017-07-23
The problem described might not quite the same as what others have reported, but having a look at the "Troubleshooting PHP 5" section [here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting_PHP_5") might provide some ideas of things to check.

---

### Post by patdundee on 2017-07-24
As an update

Some of the php works and some does not
  For example I can include a php file in an html file (default.html)  and do a mysqli query with a while loop and get a result on the php file  and get the record count.But a simple direct php entry on the html file  will not work
  code on the include php file
  ```
$result6=$conn->query("SELECT * FROM table WHERE cusID=".$_SESSION['cusID']);
$mcount=$result6->num_rows;
if ($mcount=='') {
    $mcount=0;
}
```
  in the html file i can put
  ```
echo $mcount;
```
  That works fine but if i try this is does not work
  ```
 if ($mcount == 0) {  show this html and echo $mcount;  } else { show this html  }
```
  It just shows all the html and also shows $mcount which = 0
  It is also the same result if i rename the html file to a php file and run it
  Hope that makes sense

---

### Post by patdundee on 2017-07-24
I have placed a php info page on one of the sites if anyone would like to have a look and see what i am missing (doing wrong)
[http://www.jinxphotography.co.uk/test.php](http://www.jinxphotography.co.uk/test.php)

---

### Post by lorenzopro000 on 2017-07-27
Hi,
i have a lot of php script not working with php7.

I have downgraded the php version on my server, follow this guide: [https://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04](https://askubuntu.com/questions/761713/how-can-i-downgrade-from-php-7-to-php-5-6-on-ubuntu-16-04)

---

### Post by pqwoerituytrueiwoq on 2017-07-27
what about setting php to show error messages
this shows that the setting is on line 479 of php.ini (*note this server is running 14.04)
```
chad@Z97K1LLER:~$ cat -n /etc/php5/apache2/php.ini|grep display_errors
    96    ; display_errors
   479    display_errors = On
   482    ; separately from display_errors. PHP's default behavior is to suppress those

```
also consider looking in /var/log/apache2/error.log

edit: all your php blocks start with [FONT=courier new]<?php[/FONT] not just [FONT=courier new]<?[/FONT] right?

---

