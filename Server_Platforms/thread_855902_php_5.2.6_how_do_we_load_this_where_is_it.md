---
title: "php 5.2.6 how do we load this? where is it?"
date: 2008-07-10
forum: Server Platforms
---

### Post by mspIggy on 2008-07-10
searched packages...

where is current stable php 5.2.6?

if this is not yet a package, how long does it usually take b4 these things are ready?

many thanks

iggy

---

### Post by skunkbad on 2008-07-10
I don't know if this will help, but:

[https://help.ubuntu.com/7.10/server/C/php5.html]("https://help.ubuntu.com/7.10/server/C/php5.html")

---

### Post by mspIggy on 2008-07-10
yep kind of looks liek wha ti did when i installed php -->

thsiis what i did

apt-get install libapache2-mod-php5 libapache2-mod-ruby php5 php5-common php5-curl php5-dev php5-gd php5-idn php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-mhash php5-ming php5-mysql php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl

and an old version (not current stable) was installed

this is what was installed:
PHP Version 5.2.4-2ubuntu5.1

---

### Post by windependence on 2008-07-11
5.2.4 isn't exactly "old". Unless you want to compile it, this is probably as new as you are going to get, and unless there is some reason you "need" a feature of 5.2.6 (I doubt it) there is no reason to want to do this.

-Tim

---

### Post by insaini on 2008-07-16
> **windependence said:**
> 5.2.4 isn't exactly "old". Unless you want to compile it, this is probably as new as you are going to get, and unless there is some reason you "need" a feature of 5.2.6 (I doubt it) there is no reason to want to do this.

-Tim

I believe the reason would be the couple hundred fixed since 5.2.4

---

### Post by windependence on 2008-07-16
Those fixes can be patched on the earlier version. In real life, many productions servers are still on version 4.xx

-Tim

---

### Post by insaini on 2008-07-18
> **windependence said:**
> Those fixes can be patched on the earlier version. In real life, many productions servers are still on version 4.xx

-Tim

Those production servers running 4.xx are probably not dealing with 5x or 5.2x only applications.. and being a php web app developer.. 5.3x is something im waiting for personally because of features which dont exist in 5.2x .. functions dealing with very simple introspection.. allowing for the creation of some very handy automation scripts.. and youre right.. those patches can be added over 5.2.4 .. but hah you cannot even compare 5x to 4x.. thats just wrong dude

---

### Post by cariboo on 2008-07-19
If you are always waiting for the latest and greatest because of some proposed feature, you'll never get anything done. If you really need the latest version of php you can always install from source. You can get it here:

[http://www.php.net/downloads.php](http://www.php.net/downloads.php)

Jim

---

### Post by windependence on 2008-07-20
> **insaini said:**
> Those production servers running 4.xx are probably not dealing with 5x or 5.2x only applications.. and being a php web app developer.. 5.3x is something im waiting for personally because of features which dont exist in 5.2x .. functions dealing with very simple introspection.. allowing for the creation of some very handy automation scripts.. and youre right.. those patches can be added over 5.2.4 .. but hah you cannot even compare 5x to 4x.. thats just wrong dude

Of course I never said you should purposely use 4.xx BUT, there are many times in real world situations where moving to the latest version breaks tons of code, surely you know this as a developer. I work with them all the time and there are wayyyy more 5.xx installs out there than 5.2.6. In fact I would venture to say that most places that develop php applications haven't even tested the new stuff yet. Sure, if you're just a hobbyist or learning then you should have the latest, and then IMHO you should be running it somewhere like on FreeBSD where you can compile the latest version quickly and easily.

-Tim

---

