---
title: "Apache 2 : doesnt start"
date: 2007-03-22
forum: Server Platforms
---

### Post by Arma on 2007-03-22
Hi, 

I installed Apache2 and PHP4 using :

sudo aptitude install apache2 php4 libapache2-mod-php4

but, when i try to restart the apache server, I get the following errors :

 * Forcing reload of apache 2.0 web server...                                  
grep: /etc/apache2/mods-enabled/*.load: No such file or directory
grep: /etc/apache2/mods-enabled/*.conf: No such file or directory
grep: /etc/apache2/conf.d/[^.#]*: No such file or directory
grep: /etc/apache2/mods-enabled/*.load: No such file or directory
grep: /etc/apache2/mods-enabled/*.conf: No such file or directory
grep: /etc/apache2/conf.d/[^.#]*: No such file or directory

Could anyone tell me how to fix it?
Thanks

---

### Post by gepatino on 2007-03-22
It seems like there could be some problem with the apache config directory (/etc/apache2)
try with:

sudo dpkg-reconfigure apache2

id that doesn't work:

sudo aptitude reinstall apache2 php4 libapache2-mod-php4

---

### Post by Arma on 2007-03-22
> **gepatino said:**
> It seems like there could be some problem with the apache config directory (/etc/apache2)
try with:

sudo dpkg-reconfigure apache2

id that doesn't work:

sudo aptitude reinstall apache2 php4 libapache2-mod-php4
I executed both commands, but they gave no results; I still get the same error message.

---

### Post by gepatino on 2007-03-22
have you checked permissions in /etc/apache2 and subdirs?

when you start apache, you're doing it as superuser, aren' t you?

---

