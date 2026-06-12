---
title: "apt-get install libapache-mod-php4 not available"
date: 2008-01-16
forum: Server Platforms
---

### Post by barleone on 2008-01-16
I'm new to linux, and luckily I have Google as a friend. :-P
I'm trying to set up a LAMP server with apache1+2 and PHP4+5 for some development (read: trial&error) useage.
I found a tutorial @ [**[COLOR="SandyBrown"]How To Run PHP 4 and 5 in Ubuntu Without CGI[/COLOR]**]("http://www.webhostingtalk.com/showthread.php?t=614630")
I run Ubuntu 7.10 Gutsy Gibbon.
When I was starting to install php4, apt started trowing errors:

DUTCH
user@server:~$ sudo apt-get install libapache-mod-php4
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
Pakket libapache-mod-php4 is niet beschikbaar, hoewel er naar verwezen wordt door
een ander pakket. Mogelijk betekent dit dat het pakket ontbreekt,
verouderd is, of enkel beschikbaar is van een andere bron
E: Pakket libapache-mod-php4 heeft geen installeerbare kandidaat

ENGLISH
user@server:~$ sudo apt-get install libapache-mod-php4
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package libapache-mod-php4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-php4 has no installation candidate

On several forums I found the first reaction to questions like these: Your sources.list is probably not correct. But I think it has to do with something else. Maybe the package doesn't exist at al though that would be strange.

So my question is: Does this package exist for Ubuntu 7.10 Gutsy Gibbon and if so: where from and how can I install it?
If not: what do you recommend me to do, to run Apache 1 + php4?

---

### Post by jodeet on 2008-01-16
you can use the command:

apt-cache search *packageName* to see if the package exists.

according to my gutsy-gibbon kubuntu desktop install, libapache-php4 does not exist.  You can also goto [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to check for the existence of a package in a given release.

Do you need both php4 and php5?  If not, just install php5 and apache2.

---

### Post by barleone on 2008-01-16
I've run the apt-cache search command allready. It brought me nothing but.. nothing.
Also looking on the packages-page didn't bring me any luck.

[COLOR="DimGray"]Jodeet![/COLOR] I'm looking for libapache-mod-php4, not libapache-php4. Or is that the same?

One of my friends said: "hey, maybe that package-name isn't the right one for your ubuntu. Maybe the package has another name, just try apt-cache search php4. Maybe you'll find the package then.

Well it sounded crazy to me, but I thought let's give it a try. But after I'd run the command I couldn't find the package in the list it returned.

Isn't it just crazy that Ubuntu doesn't supply this package?

Oh, and yep, I need both php-versions. I have some old code of some clients and I like it for testing php4-scripts that I find on the internet when I'm looking for something. You know... looking for some functionality and all you can find is a php4-script. Dumping it on the server and trying it is really handy instead of first converting it to php5 and then testing it.

---

### Post by andol on 2008-01-17
There is no PHP4 in Gutsy. I would guess it has something to do with the PHP-team's decision to discontinue that version. I quote from the PHP homepage. Note that the text was written last year.

> 
The PHP development team hereby announces that support for PHP 4 will continue until the end of this year only. After 2007-12-31 there will be no more releases of PHP 4.4. We will continue to make critical security fixes available on a case-by-case basis until 2008-08-08. Please use the rest of this year to make your application suitable to run on PHP 5.


If you want run PHP4 I guess your options is to compile it yourself or switch to an older version of Ubuntu. In the later case I guess 6.06 LTS (Dapper) would be a good choice.

---

### Post by jingo811 on 2008-01-17
This is how I did things in order to PHP 5 + MySQL .
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

If you need to PHP 4 and stuff read the official Ubuntu LAMP guide it's quite comprehensive.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by barleone on 2008-01-17
[COLOR="DimGray"]Andol![/COLOR] Thanks for your reply.
I knew that PHP4 will be discontinued. Though there are still enough PHP4 servers around this world.
That's why I actually can't believe that ubuntu has stopped delivering this famous package.

[COLOR="DimGray"]Jingo![/COLOR] I've read the ApacheMySQLPHP page several times, though I have a question regarding this:

> If PHP5 is present on your system, installing php4 will install the php module for apache (version 1.3) and not apache2.

How do I check whether it's installed allready? I have installed php4, so relying on this, I'd think that the apache module allready installed itself somewhere on my server.

If not, do you/someone else know where I can download and how I can compile and install the correct package? Just a link to a guide would allready help me much.

---

### Post by jingo811 on 2008-01-17
Not sure exactly what info you're trying to find but creating this file 
```
gksudo gedit /var/www/testphp.php
```
containing this code would give you some hints about what's running.
```
<?php phpinfo(); ?>
```


If not then I would try use my PHP 5 - LAMP guide and remove everything
[http://virtualseafarer.com/renaissance/desktop_lamp/chapter1.html#ch1](http://virtualseafarer.com/renaissance/desktop_lamp/chapter1.html#ch1)
then I would use this
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
to modify my PHP 5 - LAMP install into a PHP 4 equivalent.
[http://virtualseafarer.com/renaissance/desktop_lamp/chapter2.html#ch2](http://virtualseafarer.com/renaissance/desktop_lamp/chapter2.html#ch2)

---

### Post by barleone on 2008-01-18
Thanks Jingo.
It didn't help me any further, though.
I'll now first check my php4 configuration.. if it's there, it should! haha

Edits:
I haven't told you yet, but some time ago I tried this:
[COLOR="DimGray"]apt-get install libapache-mod-php4 php4-mysql apache-common php4-common apache[/COLOR]

It gave me the error written in my startpost. Now actually the first error was just a showstopper. Nothing else was executed. I figured that out when I today tried to install these packages separately.
None of the packages could be found.

After that I thought of something else.. Why wouldtn't I try sources from other ubuntu versions? So I did that and put some new entries in [COLOR="DimGray"]/etc/apt/sources.list[/COLOR]

These were the entries:
deb [http://ubuntu.apt-get.eu/ubuntu/](http://ubuntu.apt-get.eu/ubuntu/) dapper main restricted
deb [http://ubuntu.apt-get.eu/ubuntu/](http://ubuntu.apt-get.eu/ubuntu/) dapper-updates main restricted
deb [http://ubuntu.apt-get.eu/ubuntu/](http://ubuntu.apt-get.eu/ubuntu/) dapper universe
deb [http://ubuntu.apt-get.eu/ubuntu/](http://ubuntu.apt-get.eu/ubuntu/) dapper multiverse
deb [http://security.ubuntu.apt-get.eu/ubuntu](http://security.ubuntu.apt-get.eu/ubuntu) dapper-security main restricted

After that, I ran [COLOR="dimgray"]apt-get update[/COLOR]
After that, I ran [COLOR="dimgray"]apt-cache search php4[/COLOR]
It returned a lovely list of packages, and my desired packages where among them.
After that, I ran [COLOR="dimgray"] apt-get install libapache-mod-php4 php4-mysql apache-ssl apache-common libzzip-0-12 php4-common apache[/COLOR]

To configure apache I was asked for some local information to configure SSL.
And then, it crashed!

Here's the error:

> Setting up apache (1.3.34-2) ...
dpkg: error processing apache (--configure):
 subproces post-installation script returned error code 10
Setting up apache-ssl (1.3.34-2) ...
dpkg: error processing apache-ssl (--configure):
 subproces post-installation script returned error code 10
Errors found during processing of:
 apache
 apache-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)

I thought today was my lucky day but unfortunately.. It wasn't

I'm a little further, but still getting errors.
Maybe you could help me out?

---

### Post by jingo811 on 2008-01-19
Sorry I've reached the limits of my knowledge maybe somebody else knows what to do.

---

### Post by barleone on 2008-01-19
Ok.
Well, er.. HELP? Anybody out there that can help me?

---

### Post by MJN on 2008-01-19
What is it you need help with?

As mentioned above PHP4 is not available as a package in Gutsy. If you need PHP4 you'll have to compile from source.

You cannot install packages from previous releases - it doesn't work like that.

Mathew

---

### Post by barleone on 2008-01-21
Ok, then I'll try that.

---

### Post by az on 2008-01-21
PHP4 was removed from the Ubuntu archives two years ago!

PHP4 is not secure.  And are there still any applications that require php4?

I would not consider using php4 in a production environment.

Why do you need Php4?

---

### Post by jingo811 on 2008-01-23
He wanted to play with old codes that he finds on the net.  Since there's seems to be more PHP4 example codes than PHP5 on the net at this time.

---

### Post by Some_Bored_Dude on 2008-01-24
Have you tried re-configuring apache and apache-ssl?

```

sudo dpkg-reconfigure apache-ssl

```

Should then launch debconf and reconfigure the package.

No to sure. While apache-ssl was easy to get going, I've been using apache2 since 6.06.

---

### Post by JoachimDurchholz on 2008-01-28
Here's the short answer: Look at [http://pookey.co.uk/blog/archives/38-Getting-PHP4-to-work-along-side-PHP5-in-Ubuntu-Gutsy.html](http://pookey.co.uk/blog/archives/38-Getting-PHP4-to-work-along-side-PHP5-in-Ubuntu-Gutsy.html)

EDIT: The instructions look as if they should work, and they cover exactly what you want, but I haven't tested them personally. (I will have to in the next days.)

Long answer:

1) You can't have mod_php4 and mod_php5 at the same time. The modules are not designed to coexist in an Apache installation. You can, however, install both PHP versions as CGI, or one as CGI and one as Apache module.
Under Gutsy, you'd have to install PHP from sources.
2) CGI is grossly inefficient, so you don't want to install PHP-CGI on a production server.
You'd want to install mod_fcgid. mod_fcgid is relatively new, so two years ago it wasn't really usable except in very special circumstances, and the Dapper version has some awkward limitations, but any version after Dapper should be OK.
The alternative would be mod_fastcgi, which will lock up your machine with zombie processes under load on Apache2; on Apache 1.3, mod_fastcgi is OK.
3) You can't easily mix Apache 1.3 and Apache 2.x. Both want to listen on port 80, but only one can. (That's logical since web browsers request HTTP pages without caring about what server it is, so the server has no way to deciding which Apache should server the page.) The solution is the same as with PHP: compile by hand.
My personal recommendation would be to drop Apache 1.3, I never found any differences between 1.3 and 2.x that would affect PHP at the source level (there are slight but generally inconsequential differences at the php.ini level, that's all - irrelevant when testing old PHP4 scripts, I'd say).

> **az said:**
> PHP4 is not secure.  And are there still any applications that require php4?

No less secure than PHP5, I'd say.

> **az said:**
> I would not consider using php4 in a production environment.

I would not consider using PHP in a production environment. It's just too easy to build something that has SQL injection or XSS vulnerabilities, and if you use those packages that prevent these problems, all the advantages of PHP dissolve into thin air.

Unfortunately, the world being what it is, PHP is installed everywhere, so everybody who is writing web apps is writing in PHP. (Including Yours Truly.)

---

### Post by barleone on 2008-01-31
Thanks for your comments. I'll sure try some of your tips and tricks. I'm actually quite busy these days, so it might take some time before I get back on this.

As I said in my starting post, I'm using the example wherein apache1.3 + php4 and apache 2 + php5 are installed on one machine. I'm trying to reach the same setup.

It's actually just for some testing on and learning about LAMP, LAMP-maintenance and some new things like i.e. ZEND Framework.

---

