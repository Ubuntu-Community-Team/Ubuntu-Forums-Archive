---
title: "phpMyAdmin trouble"
date: 2008-05-28
forum: Server Platforms
---

### Post by Yoguess on 2008-05-28
I am running a web server on Ubuntu 8.04 with LAMP installed
i am now trying to install ampache.  i am trying to configure phpMyAdmin using [http://localhost/phpMyAdmin](http://localhost/phpMyAdmin) but I can't.  I have looked on the web and cant figure out why the config page isnt loading.  I can get to ampache page but to configure that first I have to configure php.  This is the error I get when I try to access phpMyAdmin "The requested URL /phpMyAdmin was not found on this server."

---

### Post by bluefrog on 2008-05-29
[http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

no caps for m

---

### Post by Yoguess on 2008-05-30
no that didn't work either

---

### Post by quelx on 2008-05-30
```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
```

then restart apache

like bluefrog says it will be lowercase [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by bluefrog on 2008-05-30
you have installed phpmyadmin right?

---

### Post by Yoguess on 2008-05-30
^ yes I had installed it
at server install i selected LAMP i guess p = php??

but after the ^^ above (quelx) command it now works

just a note for some newbie like me, it works with my external ip and not local host

[http://wan](http://wan) ip/phpmyadmin

i had tried that b4 but still didnt  work

Thank you guys

now can someone explain to me what i just did with the command: sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf

---

### Post by quelx on 2008-05-30
take a look at **/etc/phpmyadmin/apache.conf**

it tells apache where to find and how to treat phpmyadmin and makes an alias @ */phpmyadmin*

```
less /etc/phpmyadmin/apache.conf
```

The config needed to be in */etc/apache2/conf.d* (where the configs for web aplications live, at least in Ubuntu) so you created a symlink (**ln -s**) from the phpmyadmin config folder to the apache folder so apache could find it.  long story shortish Ubuntu does not enable web aplications by default (it's a good thing) you get a chance to configure them and then enable them by creating the symlink.

---

### Post by Yoguess on 2008-05-30
how do i change the default "no password" for root in phpmyadmin??

---

### Post by quelx on 2008-05-30
> how do i change the default "no password" for root in phpmyadmin??[http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html](http://dev.mysql.com/doc/refman/5.0/en/default-privileges.html)

---

### Post by nix4me on 2008-05-30
When you install LAMP, phpmyadmin is not installed.  You must apt-get install phpmyadmin.

From reading above, I don't think you actually have it installed.  If you do, sorry.

I am using it fine with 8.04.  Not a single problem at all.

---

