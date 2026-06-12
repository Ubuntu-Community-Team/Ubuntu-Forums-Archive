---
title: "installing php4 as well as php5"
date: 2006-06-07
forum: Server Platforms
---

### Post by nigel on 2006-06-07
I am about to install the ubuntu lamp server 6.06 for an onsite testing server and it comes with php5, 
The hosting providers for the sites i administer use php4.something, now i have read that you can install both versions of PHP (4 & 5), but one has to be installed as a cgi executible?
Now the questions start

Is this easy to do?
How do i tell my test website to use php4 rather than php5 (or vice versa)?
is there a clear succinct explanation of what it means to run it as a CGI dodacky?
as i am really confused, I do want PHP5 as it will be good to check sites for forward compatibility, especially if my hosting people switch anytime soon

Thanks in advance for anyhelp

Nigel

---

### Post by Ronbo on 2006-06-08
There is an article on howtoforge explaining this very thing for Ubuntu Breezy, I ran across it about 2 weeks ago.  It explains how to do it for Debian and Ubuntu:

[http://www.howtoforge.com/apache2_with_php5_and_php4_p2]("http://www.howtoforge.com/apache2_with_php5_and_php4_p2")

Hope this helps.

---

### Post by nigel on 2006-06-08
Thanks Ronbo 
Embarassingly enough I had actually been reading some of Falkos howtos on that site, but didn't even see that one

I'll try it out this weekend

---

### Post by adamkane on 2006-06-09
Installing php4 and php5 at the same time is difficult to pull off. 

Install the version of php you need this way. (Avoid the automatic server install):

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin]("http://localhost/phpmyadmin")

Name: root
Pass: [blank]

---

### Post by nigel on 2006-06-11
Thanks all 

Got it all working fine, running php5 with php4 as a cgi

Cheers

---

### Post by hagen00 on 2006-06-11
Just another way of doing it, which is quite simple but definitely not elegant...

If you have Apache2 with PHP 5 running and want to also run PHP 4, then you can just install Apache1 with PHP4 and have Apache1 listen on a different port such as 8080. 

hmmm :-k

---

### Post by kabam on 2006-06-14
[QUOTE=adamkane]Installing php4 and php5 at the same time is difficult to pull off. 

Install the version of php you need this way. (Avoid the automatic server install):

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
[/QUOTE]

I am very new to this (first install today).  I tried the command above for Apache2/PHP4/mySQL4 and got the message that the package PHP4 does not exist.  Have I done something wrong or does unbuntu only support PHP5 (at least without compliling PHP which I really don't want to do).

Thanks!

---

### Post by nigel on 2006-06-14
What type of install did you do?

you need to uncomment the "universe" repository

as that is where the php package is should be similar to the below
[PHP]
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
[/PHP]

---

### Post by kabam on 2006-06-15
@nigel - Thanks!  That did the trick... now I'll see if I can get everything I want installed ;) .

---

