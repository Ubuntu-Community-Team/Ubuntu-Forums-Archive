---
title: "Unblock php_uname?"
date: 2016-11-27
forum: Server Platforms
---

### Post by Heeter on 2016-11-27
Hi all,

I am trying to install an application on a LAMP ubuntu 16.04. (Roundcube webmail with plugins)

I keep getting this error when I try to run json script:

```

[ErrorException]                                    
  php_uname() has been disabled for security reasons  

```

How can I unblock this php_uname? once the application is installed, I might as well reblock it if it is really a security risk.

Thanks

---

### Post by Doug S on 2016-11-27
I have a 16.04 server with LAMP and that function seems to be working fine for me.
(Note: I tried including an example in my reply, but the system objects for unknown reasons.)

---

### Post by Heeter on 2016-11-28
Hi Doug_S

Where is this php string addressed in your system?

I looked in the /etc/php/7.0/apache2/php.ini file, but there is nothing addressing the php_uname() string in there. At least that I cannot see or search and find. maybe another file?


Regards

---

### Post by SeijiSensei on 2016-11-29
Is this a server you built?  If it's on a webhost, I'd bet uname() is disabled by the hosting company so you cannot examine the server's operating system and try to do nasty things to it. The [uname() documentation page]("http://php.net/manual/en/function.php-uname.php") doesn't say anything about security.  What if you run the script
```

<?php echo shell_exec("uname -a")?>

```
Any different?

---

### Post by Heeter on 2016-11-29
> **SeijiSensei said:**
> Is this a server you built?  If it's on a webhost, I'd bet uname() is disabled by the hosting company so you cannot examine the server's operating system and try to do nasty things to it. The [uname() documentation page]("http://php.net/manual/en/function.php-uname.php") doesn't say anything about security.  What if you run the script
```

<?php echo shell_exec("uname -a")?>

```
Any different?

Hi, I am running my own LAMP 16.04 with postfix and dovecot, full access to machine and admin.

This is what I am getting
```

root@mailserv:/home/admin# <?php echo shell_exec("uname -a")?>
bash: syntax error near unexpected token `('
root@mailserv:/home/admin# 

```

Regards

---

### Post by Doug S on 2016-11-30
The system would not let me post my file last time, I'll try again:

Nope. Still will not allow it. Grrrr...

---

### Post by SeijiSensei on 2016-11-30
You can't just run a PHP script from the command prompt.  You need to use the php binary or put it in a PHP script on the web.

From the command prompt:
```

$ php -r 'echo shell_exec("uname -a");'
Linux xxx.xxx.com 4.8.3-x86_64-linode76 #1 SMP Thu Oct 20 19:05:39 EDT 2016 x86_64 x86_64 x86_64 GNU/Linux

```

I put this script in /var/www/html/test.php of this 14.04 machine (called "linux-tv") that runs Apache:
```

<?php

echo "<p>Using the php_uname() function</p>";
echo "<pre>".php_uname()."</pre>";

echo "<p>Running uname from the shell</p>";
echo "<pre>".shell_exec("uname -a")."</pre>";

?>

```

Here is the result of [http://localhost/test.php:](http://localhost/test.php:)
```

Using the php_uname() function

Linux linux-tv 3.13.0-101-generic #148-Ubuntu SMP Thu Oct 20 22:08:32 UTC 2016 x86_64

Running uname from the shell

Linux linux-tv 3.13.0-101-generic #148-Ubuntu SMP Thu Oct 20 22:08:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by Doug S on 2016-12-09
Note: At this point, this post is more about [the posting issues thread]("https://ubuntuforums.org/showthread.php?t=2331266&page=29&p=13580813#post13580813") than anything else.

I think I figured out how to post the file I had been trying to post herein previously:```
doug@DOUG-64:~/public_html/php$ [COLOR="#FF0000"]cat test4.php[/COLOR]
< h t m l >     [COLOR="#FF0000"]<<<< The spaces are so that this reply will actually work[/COLOR]
<head>
<title>Test PHP Program</title></head>
</head>
<body>
<?php
echo 'Hello word !<BR>';
echo php_uname();
echo '<BR>';
echo PHP_OS;
echo '<BR>';
?>
</body>
</html>

```

---

### Post by Graham_Willis on 2016-12-11
Heeter: create phpinfo.php file with the following contents:

```

<?php

phpinfo();

?>

```

preferably in the directory in which RoundCube's about to be installed and then load the corresponding page. It'll help you to figure out what PHP configuration file is. Then go there and grep it against "php_uname" phrase, delete it from the list of forbidden functions and reload PHP. Of course - generally speaking it's better to have this function turned off, so my advice's is to disable it immediately after you're done.

---

