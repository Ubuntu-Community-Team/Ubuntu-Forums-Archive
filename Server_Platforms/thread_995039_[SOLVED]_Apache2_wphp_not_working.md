---
title: "[SOLVED] Apache2 w/php not working"
date: 2008-11-27
forum: Server Platforms
---

### Post by angstsix on 2008-11-27
Hello,

I've just setup a new server using ubuntu server.
Apache is running and I've installed php5 and reloaded the server.
however when i try to load a php file from the server it prompts me to download the file.

hope someone here might have an idea as to what I've done wrong, or If i need to install some additional software to make this run?

thanks in advance for your time!

---

### Post by ianhaycox on 2008-11-27
Try running

```

sudo a2enmod php5

```

and then verify that 

```

ls /etc/apache2/mods-enabled/

```

has the php5 modules enabled.

You might need to restart apache and check the log files

```

sudo /etc/init.d/apache2 restart
more /var/log/apache2/error.log
more /var/log/apache2/access.log

```

---

### Post by angstsix on 2008-11-27
nice! your the man! running:
```
a2enmod php5
```
worked!

what exactly does this do?

---

### Post by ianhaycox on 2008-11-27
It's a perl script that basically creates links from the /etc/apache2/mods-available/ to the /etc/apache2/mods-enabled/ directory.

You can use the ln -s command yourself but it's easier.

---

### Post by angstsix on 2008-11-27
ah i see.
thanks again!

---

