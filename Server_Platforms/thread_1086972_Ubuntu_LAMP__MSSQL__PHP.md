---
title: "Ubuntu LAMP | MSSQL | PHP"
date: 2009-03-04
forum: Server Platforms
---

### Post by ethos84 on 2009-03-04
Hi guys

I don't seen to be getting anywhere with this having searched for guides / a way to get this up and running.

Could someone point me in a direction of a guide or explain how to get a connection to a MS SQL server up and running? We're looking to query with php.

The box is already running our intranet (php/mysql/apache) so ideally that would need to go untouched.

Any help welcome.

Please don't just post "freetds" or "obdc"! 

Thanks:)

---

### Post by ethos84 on 2009-03-09
Bump :-({|=

---

### Post by LegendofTom on 2009-03-09
I would try this:

[http://driftharmony.wordpress.com/2008/08/15/connecting-ubuntu-804-to-microsoft-sql-server/](http://driftharmony.wordpress.com/2008/08/15/connecting-ubuntu-804-to-microsoft-sql-server/)

---

### Post by ethos84 on 2009-03-25
Doesn't seem like a fairly solid guide and misses out some bits from what I can see, thanks for linking though.

Anyone else? :)

---

### Post by ehudokai on 2009-03-25
Pretty simple:

aptitude install php5-mssql.

Then look at the documentation on how to connect and query using the mssql database driver for php: [http://us3.php.net/mssql]("http://us3.php.net/mssql")

Or even better get a php database abstraction layer like [adodb]("http://phplens.com/adodb/").

Happy coding :)

---

### Post by ethos84 on 2009-03-25
Thanks mate.

Interesting if I run that command it shows;

0 packages upgraded, 0 newly installed, 105 to remove and 56 not upgraded.
Need to get 0B of archives. After unpacking 121MB will be freed.

Bit strange? :D

---

### Post by mrsteveman1 on 2009-03-26
run these to update the system first:
```
apt-get update && apt-get upgrade
```

Then try installing the package for php-mysql again

If you need help getting it working i can help out, however i'm not a programmer just a lowly system administrator :)

---

### Post by daboroe on 2009-03-26
Can I ask why you are not using MySQL and MSSQL? In my experience MySQL is a little more stable, etc. 

Also a suggestion to install phpmyadmin after you get everything up and  running so you havea  "GUI" interface do deal with databases no matter if it is MySQL or MSSQL.

---

### Post by ethos84 on 2009-03-26
Because we have multiple databases setup on mssql and everything that uses them runs fine. To convert to mysql would just an uneeded headache. Plus MSSQL is better supported. 

We have our intranet running off MySQL and using phpmyadmin with no issues, but would like the ability to be able to query our MSSQL database from the intranet (using php). 

Still haven't got anywhere with this either :(

---

### Post by MystaMax on 2009-03-26
Are you having troubles using the package? Or are you having troubles installing it? 

ehudokai forgot one important thing with his suggestion. The sudo command. Make sure you are you typing:

```
 sudo aptitude install php5-mssql 
```you can check to see if its installed with:

```
 dpkg -l | grep mssql 
```

---

### Post by ethos84 on 2009-03-26
Both essentially. All I want to achieve for the moment is to connect to mssql and query tables in a database for example.

If I run sudo aptitude install php5-mssql I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 63 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

If I grep I don't get any output...

---

### Post by ethos84 on 2009-03-30
Bump! :)

---

### Post by windependence on 2009-03-30
[http://jlac1024.vox.com/library/post/mssql-support-with-php.html](http://jlac1024.vox.com/library/post/mssql-support-with-php.html)

BTW, MSSQL is better supported than MySQL? I think that's highly debatable. Maybe by Micro$oft, but not generally. Almost every data driven app using PHP on the web uses MySQL, and there is a commercial version in sace your IT dept wants to spend money for support. Sun is the company behind it.

-Tim

---

### Post by ethos84 on 2009-03-30
> **windependence said:**
> [http://jlac1024.vox.com/library/post/mssql-support-with-php.html](http://jlac1024.vox.com/library/post/mssql-support-with-php.html)

-Tim

Thanks Tim.

I get this when trying to configure php:

Sorry, I cannot run apxs.  Possible reasons follow:

1. Perl is not installed
2. apxs was not found. Try to pass the path using --with-apxs2=/path/to/apxs
3. Apache was not built using --enable-so (the apxs usage page is displayed)

---

### Post by ethos84 on 2009-03-30
Going to install "apache2-threaded-dev" ...

I still don't have an apache folder in /usr/local though.

If I change * --with-apxs2=/usr/local/apache2/bin/apxs \* to *--with-apxs2=/usr/bin/apxs2 \ *it runs but I get *configure: error: libpng.(a|so) not found* at the end. 

I'm surprised there isn't a propery package for this!

---

### Post by windependence on 2009-03-30
Apache is not installed correctly is my guess. You should have an apache2 folder in /usr/local.

-Tim

---

### Post by ethos84 on 2009-03-30
It's running fine, i've also checked my linode with a live website and it also doesn't have a /usr/local/apache2!

---

### Post by MystaMax on 2009-03-30
Just thought I'd post these two links:

1. [http://bit.ly/Dqf1L](http://bit.ly/Dqf1L)
2. [http://bit.ly/FuGMw](http://bit.ly/FuGMw) 

The 1st is to a bug report concerning the php5-mssql. Lots of good information pertaining to your problem. The 2nd is to a blog post where bug reporters stated it allowed them to use php5-mssql properly, but would break upon updating php.

Right now, it looks like compiling from source is your only option. Which I assume you're attempting from the link Tim posted.

---

### Post by ethos84 on 2009-04-01
Yeah.

It seems there are no "guides" that actually work?

---

### Post by ActiveFrost on 2009-04-01
LAMP installation ( apache, php, mysql, phpmyadmin ) : [http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100) ;)

---

### Post by ethos84 on 2009-04-01
> **ActiveFrost said:**
> LAMP installation ( apache, php, mysql, phpmyadmin ) : [http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100) ;)

I'm looking for MSSQL not MYSQL ;)

---

### Post by ethos84 on 2009-04-01
I've followed this guide:

[http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/](http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/) and installed php5-mssql_5.2.6-2ubuntu4.1_i386.deb.

How do I test this out though? :-k

---

### Post by LordDragoonXVI on 2009-05-24
Hello
I see you have stopped responding to this post hopefully you had better luck then me. I have been having the same exact issue. I have been trying to install support for MSSQL data connection using PHP, and after about two months still have not been able to get it to work. MySQL works fine everything else works fine, I can even use other Ubuntu programs to talk to the MSSQL server just not PHP. I have tried most of the guides here and else where on the web with no luck. 

Well I am going to take a look at the bug reports posted above and see if they can help me and I will post back if they do. 

Good luck to anyone else with problems^^

---

### Post by atomicarena on 2009-05-29
> **LegendofTom said:**
> I would try this:

[http://driftharmony.wordpress.com/2008/08/15/connecting-ubuntu-804-to-microsoft-sql-server/](http://driftharmony.wordpress.com/2008/08/15/connecting-ubuntu-804-to-microsoft-sql-server/)


I would recommend following [this site]("http://www.howtoforge.com/ubuntu_debian_lamp_server") to check on set up of LAMP in UBUNTU. it was just seamless setup for me. 

Thanks
Praveen Kannan

---

