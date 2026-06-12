---
title: "I have 2 php.ini files, and I dont know what one to change, or why I have 2"
date: 2010-06-12
forum: Server Platforms
---

### Post by rhythmiccycle on 2010-06-12
trying to send email from php
I'm hosting a website from my pc.

LAMP is installed, and php and mysql is running fine.


i want the web site to send automated e-mails

i found the code

mail($to,$subject,$message,$headers);

but its not working.

I'm pretty sure i need to configure the php.ini file, but the problem is I have 2 php.ini files, and I dont know what one to change, or why I have 2

the two files with path are :


/etc/php5/apache2/php.ini
/etc/php5/cli/php.ini


why is there two?
what one do I need to change?

(i have other questions, but first things first)

---

### Post by Ryan Dwyer on 2010-06-12
PHP can be run using Apache, or directly as a program. The php.ini in the apache2 directory is used when PHP is being run as an Apache module, so you'll probably want to edit that one. The php.ini in the cli directory is used if you're running a script with `php scriptname` or using php -a.

---

### Post by Ryan Dwyer on 2010-06-12
With your mail problem, replace your mail line with this:

ini_set('display_errors','on');
error_reporting(E_ALL);
var_dump(mail($to,$subject,$message,$headers));

If you see bool(true), then the mail server accepted the message but might have discarded it after closing the connection, or maybe the message is still being delivered.

If it says bool(false) then it flat out rejected it and you should also see the error message describing the reason.

---

### Post by dapperdanny77 on 2010-06-13
hi,

you can create a php which is put in your apache tree - executing this shows you the config of your apache-php settings


```

<?php

phpinfo();

?>

```

[http://php.net/manual/en/function.phpinfo.php]("http://php.net/manual/en/function.phpinfo.php")

---

### Post by rhythmiccycle on 2010-06-16
I used phpinfo(); to verify that is is infact:
/etc/php5/apache2/php.ini


> **Ryan Dwyer said:**
> 

If it says bool(false) then it flat out rejected it and you should also see the error message describing the reason.

it returns bool(false);

i'm going to try to change the php.ini now, and will post how it goes.

---

### Post by rhythmiccycle on 2010-06-16
I had all kinds of issues with the mail() function,

But I found PEAR as a simpler way to achieve what I'm going for

I posted what I did here

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9468939#post9468939](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9468939#post9468939)

---

