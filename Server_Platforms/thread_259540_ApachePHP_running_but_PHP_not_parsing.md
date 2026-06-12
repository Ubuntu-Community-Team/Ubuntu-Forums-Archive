---
title: "Apache/PHP running but PHP not parsing"
date: 2006-09-17
forum: Server Platforms
---

### Post by locoHost on 2006-09-17
When I enter [http://localhost](http://localhost) in FF, I see a list of files and at the bottom is this...


Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80


This tells me Apache and PHP are both running. However my PHP files are not parsing. When I enter URL to an existing PHP file, it tries to start a download of that file. What does this mean?

Thanks for your help :-)

---

### Post by L0c0 on 2006-09-17
Hi,

In /etc/apache2/apache2.conf find the line that reads:

#AddType application/x-httpd-php .php

and uncomment it so it reads:
AddType application/x-httpd-php .php


HTH,

L0c0

---

### Post by locoHost on 2006-09-17
L0c0 you're a genius!
 
That was your first post too. You're batting 1000!

Thank you!

---

### Post by BigDaddyEBK on 2007-02-04
This helped me a lot!

:oops:

---

### Post by lobo-tuerto on 2008-01-16
Where would you put that line for Apache2 in Ubuntu 7.10?

Because that line doesn't exist in that file anymore :(

---

### Post by scizzo on 2008-01-16
> **lobo-tuerto said:**
> Where would you put that line for Apache2 in Ubuntu 7.10?

Because that line doesn't exist in that file anymore :(

Do you really have the package:

libapache2-mod-php5

installed?

Since that should be pretty much all you need to get for it to run in apache2. After restarting the apache2 server that is.

---

### Post by scizzo on 2008-01-16
If you do have it installed:

Check in /etc/apache2/mods-available/ for the files php5.conf and php5.load

You can also check so that they are in the mods-enabled folder.

NOTE: php5.conf includes the AddType

---

### Post by MJN on 2008-01-16
> **scizzo said:**
> You can also check so that they are in the mods-enabled folder.
 
Not 'can', but **must**!
 
Modules are not enabled until they are symlinked from mods-enabled - merely existing in mods-available is insufficient (since that folder is not directly parsed).
 
Mathew

---

### Post by lobo-tuerto on 2008-01-16
Thanks guys, problem solved ;)

---

### Post by Gangles on 2008-01-21
Hello,

I am having the same problem (php script not parsing in Firefox), but unfortunately the term "sym-linked" is a little over my head!

php5.conf and php5.load are present in both my mods-available and mods-enabled folders. Could I get a simple explanation as to what I should do next?

Regards

---

### Post by nectarine on 2008-01-29
sym-linked, means symbolic links. 
You need to make sure that there are symbolic links from
/etc/apache2/mods-enabled/php5.conf   to  /etc/apache2/mods-available/php5.conf
and
/etc/apache2/mods-enabled/php5.load   to  /etc/apache2/mods-available/php5.conf

symbolic links are files that act like pointers to other files. details and examples are here:
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)

---

### Post by Gangles on 2008-01-31
I've checked, and the php5.load and php5.conf files in mods-enabled are properly symlinked to mods-available. That must not be the root of my problem :(

Does anyone else have other ideas as to why Firefox wouldn't want to run a PHP script? :confused:

---

### Post by nectarine on 2008-01-31
Just to clarify, php is server side, so it's not firefox that doesn't want to run it. It's apache.

Um.. no sorry, I'm not really an expert, but let me think about it a bit.

---

