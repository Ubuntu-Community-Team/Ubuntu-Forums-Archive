---
title: "Restrict login url to certain ip's only."
date: 2009-12-15
forum: Security
---

### Post by zhelev81 on 2009-12-15
i have an admin login page where i'm the only one who suppose to log in ... so I want to restrict this page wich is on the local host to 2 or 3 ip-s only ,how to do this ?

My linux is Xubuntu and I'm very neew to this stuff ... so pls explane me the steps i have to do ..


tnx in advance :popcorn:

---

### Post by bodhi.zazen on 2009-12-15
[http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/](http://www.cyberciti.biz/faq/apache-restrict-access-based-on-ip-address-to-selected-directories/)

That should point you in the right direction I hope ;)

---

### Post by needhelppeeps on 2009-12-16
Hopefully I understand what question you ask. 

I used to have a joomla site. To restrict IPs to that admin folder, I created an .htaccess file which only allowed access to that folder from one IP,, then in the main folder that .htaccess folder only had the standard options which blocked China, Russia, and known problematic ranges. 

So answer is create an .htaccess file, allow only those ips, put said file in relevant folder.

---

### Post by zhelev81 on 2009-12-16
this is not a dir so ... your solutions are not goood for me ... this is a url ... link look here :

[http://www.ctfstats.com/hlstats.php?mode=admin](http://www.ctfstats.com/hlstats.php?mode=admin)

i want to restrict access only to this page og the site ... all other pages to be available to anyone ... if i restrict the dir ,this means i will restrict the players to see their score ,i hope that expalned it now ;)

---

### Post by EJeanmaire on 2009-12-17
> **zhelev81 said:**
> this is not a dir so ... your solutions are not goood for me ... this is a url ... link look here :

[http://www.ctfstats.com/hlstats.php?mode=admin](http://www.ctfstats.com/hlstats.php?mode=admin)

i want to restrict access only to this page og the site ... all other pages to be available to anyone ... if i restrict the dir ,this means i will restrict the players to see their score ,i hope that expalned it now ;)


Let me explain some important concepts about a URL construct:

[http://www.ctfstats.com/hlstats.php?mode=admin](http://www.ctfstats.com/hlstats.php?mode=admin) is one file.... hlstats.php

[http://www.ctfstats.com/hlstats.php?mode=WHOCARES](http://www.ctfstats.com/hlstats.php?mode=WHOCARES) is the same file

[http://www.ctfstats.com/hlstats.php](http://www.ctfstats.com/hlstats.php) again, is the same file...

php takes certain parameters out of the URL construct which are assigned as variables, long story short, what you are trying to do cannot be accomplished with file permissions because your site is only ONE file.  The user section and the admin section, its all part of the php code inside taht one file, meaning php itself will have to handle authentication of the "admin" section.

---

