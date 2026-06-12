---
title: "Strange Apache fopen permissions problem."
date: 2005-03-28
forum: Server Platforms
---

### Post by iso on 2005-03-28
I'm having some problems with apache not being able to write files. The following is some php code that creates and writes some data to a file. However, when i run it, i get the following error.

```
<?
$fp = fopen("my.log","a");
$str = date("Y-m-d H:i:s") . ".  code : " .$error_code . "." ;
fwrite ($fp,$str . "\r\n");
 fclose($fp);
?>
```

Warning: fopen(my.log): failed to open stream: No such file or directory in /var/www/legos/htdocs/write.php on line 2

Warning: fwrite(): supplied argument is not a valid stream resource in /var/www/legos/htdocs/write.php on line 4

Warning: fclose(): supplied argument is not a valid stream resource in /var/www/www.fightemo.com/htdocs/write.php on line 5


```
root@dante:/var/www/legos# ps -Af |grep apache
root     11772     1  0 Mar23 ?        00:00:00 /usr/sbin/apache2 -k start -DSSL
www-data 19916 11772  0 12:54 ?        00:00:03 /usr/sbin/apache2 -k start -DSSL
www-data 20458 11772  0 13:42 ?        00:00:02 /usr/sbin/apache2 -k start -DSSL

``` 

open_basedir is not specified
php is not running in safe-mode

drwxrwxrwx 15 www-data www-data 4096 2005-03-20 15:14 var
drwxrwxrwx 5 www-data www-data 4096 2005-03-23 02:12 www

groups www-data 
www-data : www-data

Linux dante 2.6.8.1-5-686-smp #1 SMP Mon Mar 14 21:59:14 UTC 2005 i686 GNU/Linux

---

### Post by dseomn on 2005-03-28
First, try using an absolute path for the log file. If that works, it just means you weren't in the pwd you could you were. If it doesn't work, make sure the file exists.

---

### Post by iso on 2005-04-02
I have tried using the full path to the file, however, that does not work. If i create (touch) the file and give it proper permissions, it is able to execute without problem, however, it will not create it on its own.  

I tried running this code on a default fedora install with apache-php and it is able to create the file and execute without problem.

I have also experienced strange behavior while installing linpha which is a photo album that runs on php/mysql/apache.  When it tries to write the config file, i get the same result.  In addition, while installing pear pluggins, "pear install Auth-beta" i get the following error. 

downloading Auth-1.3.0r3.tgz ...
could not open /tmp/tmpbKgox9/Auth-1.3.0r3.tgz for writing

I believe these problems are related since pear is dependent on php.

> If that works, it just means you weren't in the pwd you could you were. If it doesn't work, make sure the file exists.

what do i have to do with the pwd? i'm not sure i follow.

thanks for your help.

---

### Post by CrustyDOD on 2005-04-02
OK, why don't you just create manually empty log file? Then it should work...

---

### Post by iso on 2005-04-02
[QUOTE=CrustyDOD]OK, why don't you just create manually empty log file? Then it should work...[/QUOTE]

I am using the code to illustrate a server wide problem i am having which is associated with PHP's current inability to create and write to new files.  The problem ends up being, that i must manually create every file that I want php to write to.  Is this proper behavior of PHP?  The pear problem illustrates this same behavior as well.  Thanks for taking a look.

---

### Post by CrustyDOD on 2005-04-03
Well i tested the code and it works for me, creates a file if the file doesn't exist if i change my folder permissions to 777 instead of 755...

---

### Post by iso on 2005-04-03
[QUOTE=CrustyDOD]Well i tested the code and it works for me, creates a file if the file doesn't exist if i change my folder permissions to 777 instead of 755...[/QUOTE]

What build are you using?  I found that my other server isn't having this problem and noticed the different builds.

(problem) Linux Dante 2.6.8.1-5-686-smp #1 Mon Mar 14 21:59:14 UTC 2005 i686
(works)    Linux Randall 2.6.8.1-3-386 #1 Thu Nov 18 11:47:33 UTC 2004 i686

I upgraded the kernel on the older box.  Hm, the problem doesn't seem to follow the kernel either.

---

### Post by CrustyDOD on 2005-04-04
Linux version 2.6.8.1-3-386  :)

---

### Post by iso on 2005-04-07
Problem resolved..

apt-get install linux-686-smp

---

