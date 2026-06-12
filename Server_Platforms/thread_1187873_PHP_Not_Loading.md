---
title: "PHP Not Loading"
date: 2009-06-15
forum: Server Platforms
---

### Post by zaaaaaac on 2009-06-15
Hey, I installed Ubuntu Server (latest) and LAMP and all that. But my problem is when i go to [http://192.168.1.9](http://192.168.1.9) (Local ip of the server) i get this prompt:

[[IMG]http://img200.imageshack.us/img200/8128/90205432.png[/IMG]]("http://img200.imageshack.us/i/90205432.png/")

---

### Post by ActiveFrost on 2009-06-15
```
sudo apt-get install php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart
```

---

### Post by zaaaaaac on 2009-06-15
Thanks, but that didn't work. It seems that it works in IE. I didn't test it before hand, but it works in IE now. Although, I would very much like it to work in FF.

---

### Post by smeerbartje on 2009-06-15
> **zaaaaaac said:**
> Thanks, but that didn't work. It seems that it works in IE. I didn't test it before hand, but it works in IE now. Although, I would very much like it to work in FF.

When it works in IE --> it works. I think it has to do with caching. Please clear firefox' cache/saved cookies/all the **** and try again.

---

### Post by ActiveFrost on 2009-06-15
As previously said, if it works on IE, it works on ALL browsers ! There should be something misconfigured in your Firefox. Any chances to get your servers IP/domain to test this out ( just want to check if I'll get the same output ) ?

---

### Post by budluva04 on 2009-06-15
hi, i don't know if you have solved this problem already...

but you need to add the php mimetype to apache so i can parse php properly...

```
sudo nano /etc/apache2/apache2.conf
```

then add this to end of apache2.conf

```
AddHandler application/x-httpd-php php
```

then restart apache

```
sudo /etc/init.d/apache2 restart

```
then flush your browser's cache and have fun :P

---

### Post by zaaaaaac on 2009-06-16
Thanks everyone. And thanks badluva04 for giving me the solution.

---

### Post by budluva04 on 2009-06-16
haha no problem, BUT IM NOT A BADLUVA!!! :P i don't get comlaints from the women :P

---

### Post by mbeach on 2009-06-16
just a note to anyone coming here for a solution - it might be better to ensure php5 is enabled, 
```
sudo a2enmod php5
```
and the AddHandler line bud mentioned will be in:
/etc/apache2/mods-enabled/php5.conf
which will get loaded by apache.

essential reading:
/usr/share/doc/apache2/README.Debian.gz

---

