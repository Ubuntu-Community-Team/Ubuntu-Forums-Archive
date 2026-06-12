---
title: "Downgrade PHP5 to PHP4"
date: 2006-08-01
forum: Server Platforms
---

### Post by raoulw on 2006-08-01
Hi All,

I'm new to Ubuntu but an old linux hand (debian 2.0.34 was my first (omg - that was 10 years ago!!!)).

I've just setup a LAMP server and got all our virtual servers nicely setup only to find out PHP5 in installed. Our old server has PHP4 (as do our clients hosted sites).

Not wanting to spend weeks rewritting code (or getting into a flame war over php4 vs php5 :), I'd like to know if there's a quick way to downgrade without breaking apache2.

I saw that PHP5 is a meta package so I thought a quick post (after my goooolging with no result) would be quickest.

Thanks & regards,
Raoul

---

### Post by adamkane on 2006-08-01
I've had success by installing the new version that I want. The old version is automatically uninstalled.

The problem is when Ubuntu updates the php/mysql packages, and everything breaks, and re-install is required. PITA!

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
Reboot (or start apache and mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by pdc303 on 2006-08-01
you do not need to 'downgrade'. PHP4 and PHP5 can run side-by-side very happily.

Make sure apache loads the PHP4 and PHP5 modules then it is simply a case of choosing which engine parses your files.

You can set your 'default' handler in your apache conf file by the 'AddType' directive.
You could even set .php4 files to be parsed by PHP4 and .php5 files by PHP5.

Also, you can use the 'AddHandler' directive in .htaccess files if you wish to use another version of PHP to parse your PHP scripts.

Just a thought for your situation.

---

### Post by adamkane on 2006-08-02
That works too. There is a howto on howtoforge.com

---

### Post by az on 2006-08-02
> **pdc303 said:**
> you do not need to 'downgrade'. PHP4 and PHP5 can run side-by-side very happily.

No.  You cannot install both the libapache2-mod-php4 and libapache2-mod-php5 packages at the same time.  It's one or the other.


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
See what happens when you try to install both:
[https://help.ubuntu.com/community/ApacheMySQLPHP/AptPhp4Output](https://help.ubuntu.com/community/ApacheMySQLPHP/AptPhp4Output)
you end up with libapache2-mod-php5 and libapache-mod-php4.  Apache2 is the current version of apache and apache refers to apache1.3 -  Since only one instance of apache can run PHP at once, you get apache and apache2 installed simultaneously.  That's not what you want.

The quick way to get apache2 to use php4 is to substitude libapache2-mod-php5 with the php4 package.

Make sure you have universe enabled and run

sudo apt-get install libapache2-mod-php4 libapache2-mod-php5-

The minus sign will mark that package for removal and remove it.  Apache2 will end up running php4.

---

### Post by az on 2006-08-02
> **adamkane said:**
> 
The problem is when Ubuntu updates the php/mysql packages, and everything breaks, and re-install is required. PITA!


It's much easier to just fix the problem than to re install.

A re-install is usually only required when you have had a security breach or hardware failure.

---

### Post by adamkane on 2006-08-03
Agreed, but I've never come across a thread about how to re-install successfully. I'm keeping my eyes open though.

Here's the howtoforge link:
[http://www.howtoforge.com/apache2_with_php5_and_php4](http://www.howtoforge.com/apache2_with_php5_and_php4)

---

### Post by az on 2006-08-03
> **adamkane said:**
> 
Here's the howtoforge link:
[http://www.howtoforge.com/apache2_with_php5_and_php4](http://www.howtoforge.com/apache2_with_php5_and_php4)

Sure, but most of the time, you want both php4 and php5 to run different web applications.  I don't think you can run them with a version of php as CGI.  I think you would have to hack them to do so, no?

---

### Post by adamkane on 2006-08-04
Correct. I certainly don't recommend running php4 and php5 at the same time. It's unnecessarily convoluted. I would just use 2 machines rather than run them both at the same time on the same machine.

---

