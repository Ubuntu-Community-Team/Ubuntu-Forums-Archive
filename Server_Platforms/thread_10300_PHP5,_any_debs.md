---
title: "PHP5, any debs?"
date: 2005-01-06
forum: Server Platforms
---

### Post by HiddenWolf on 2005-01-06
Is there any chance we'll see some PHP5 support soon?

I'm coding a new website, and altho the server is now running ISS/PHP4, if this project works out It'll be an Apache2/Php5 server preferably.
I'd rather not install vanilla packages.

---

### Post by jdong on 2005-01-06
Experimental packages have been released from Debian. Not production quality, duh!

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=jdong]Experimental packages have been released from Debian. Not production quality, duh![/QUOTE]

I'd still like to see how my code would behave.
I'm coding right now. And I don't fancy doing it over again in a few months because it doesn't work on PHP5. :-)

How far along are they?

---

### Post by DJ_Max on 2005-01-15
I'm looking for PHP5 as well, so I did a search on these boards and found a few people recommend [http://www.dotdeb.org/](http://www.dotdeb.org/) . But currently their PHP5 deb only works with Apache 1.3.

Unless this is what you mean by "vanilla packages" as I'm not sure what you mean by that statement. :oops:

---

### Post by Artiom on 2005-01-15
if you just want to check how code works on php5 & apache 2, you can try :[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by downtime on 2005-03-01
i got the source .deb from dotdeb.org and i'm trying to install it with Apache2 on the AMD64 distro. i'm working my way through the compile, but i'm stuck on "configure: error: PNG support requires ZLIB. Use --with-zlib-dir=<DIR>" and can't past that. i've got zlib1g and zlib1g-dev installed, but i can't get the configure to see it. 

i have --with-zlib and --with-zlib-dir=/usr in the rules file. i need zlib support for png for GD.

has anyone else had luck getting php5 on this configuration?

---

### Post by Jad on 2005-03-01
apache friends XAMP is good for development, you can switch from PHP4 to php5 with one simple command

---

### Post by jdonnell on 2005-03-01
You should compile it from source. It's not too hard, I've done it a few times on my mac os x machine. It's better to use apache2.

---

### Post by Jad on 2005-03-02
Why its better to use apache2 for development?

---

### Post by hantsy on 2005-03-02
[QUOTE=DJ_Max]I'm looking for PHP5 as well, so I did a search on these boards and found a few people recommend [http://www.dotdeb.org/](http://www.dotdeb.org/) . But currently their PHP5 deb only works with Apache 1.3.

Unless this is what you mean by "vanilla packages" as I'm not sure what you mean by that statement. :oops:[/QUOTE]
Php5 is in debian sid now , it can work with apache 1.3 or  apache 2  through a module named libapache_mod_php5(for apache 1.3.x) or libapache2_mod_php5(for  apache2 )..

---

### Post by jdonnell on 2005-03-02
[QUOTE=Jad]Why its better to use apache2 for development?[/QUOTE]

I meant that there is more info for using/installing php5 with apache2. Not that apache2 is better for development. If you don't have a specific reason to use 1.3 then why not use the newest version?

---

### Post by DarkSilver on 2005-03-20
I've made a little tutorial here : [http://www.ubuntulinux.org/wiki/PHP5FromSource]("http://www.ubuntulinux.org/wiki/PHP5FromSource")
PHP5 from source with apache2...

---

