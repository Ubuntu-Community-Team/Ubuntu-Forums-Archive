---
title: "apache language"
date: 2008-10-08
forum: Server Platforms
---

### Post by divinequran on 2008-10-08
Hi,

I copied some arabic text into a php file
<?php
$new = "arabic text";
echo "$new";
?>

and printed those values on my browser, it doesnot print those values properly, i uploaded the same file on a website and the same browser prints those values propely, what is the problem with webserver. is this is some thing related to AddLanguages in apache, how to fix this issue?

---

### Post by cdenley on 2008-10-08
> **divinequran said:**
> Hi,

I copied some arabic text into a php file
<?php
$new = "arabic text";
echo "$new";
?>

and printed those values on my browser, it doesnot print those values properly, i uploaded the same file on a website and the same browser prints those values propely, what is the problem with webserver. is this is some thing related to AddLanguages in apache, how to fix this issue?

I'm not sure because I've never had to use a different character set, but you may want to look at:
/etc/apache2/conf.d/charset
[http://us3.php.net/manual/en/function.http-negotiate-charset.php](http://us3.php.net/manual/en/function.http-negotiate-charset.php)

---

### Post by divinequran on 2008-10-23
I have searched in /etc
i can find the folder called /etc/httpd/conf/httpd.conf but not anything called charcterset, how to make those language to get supported on my local machine

---

### Post by cdenley on 2008-10-23
What are you running?
```

cat /etc/lsb-release
dpkg -l|grep apache

```

---

### Post by divinequran on 2008-11-04
I cant find dpkg command, I am using apache 2

---

### Post by cariboo on 2008-11-05
Just type the  command in a teminal:

```
dpkg -l|grep apache
```

it should return something like this:

```
dpkg -l|grep apache
ii  apache2                               2.2.8-1ubuntu0.3                         Next generation, scalable, extendable web se
ii  apache2-mpm-prefork                   2.2.8-1ubuntu0.3                         Traditional model for Apache HTTPD
ii  apache2-utils                         2.2.8-1ubuntu0.3                         utility programs for webservers
ii  apache2.2-common                      2.2.8-1ubuntu0.3                         Next generation, scalable, extendable web se
ii  libapache2-mod-php5                   5.2.4-2ubuntu5.3                         server-side, HTML-embedded scripting languag
```

Jim

---

### Post by cdenley on 2008-11-05
> **divinequran said:**
> I cant find dpkg command, I am using apache 2

I reason I asked for that output is because apache2 in ubuntu doesn't use the path "/etc/httpd/conf/httpd.conf", and as far as I know it never did.

---

### Post by divinequran on 2008-12-09
yes it is not ubuntu it is in redhat machine, i have no problem with ubuntu i installed lamp in and it works fine in redhat machine, but still i cant resove the issue in my redhat machine. i have also added



AddLanguage ar .ar



under add language but it failed. i don't know what the reason.

---

