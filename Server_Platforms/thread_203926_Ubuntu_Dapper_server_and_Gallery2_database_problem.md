---
title: "Ubuntu Dapper server and Gallery2 database problem"
date: 2006-06-26
forum: Server Platforms
---

### Post by SilvioTO on 2006-06-26
I'm trying to install gallery2 but at step 5 (database configuration) receive this error message:

Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server during query in /var/www/gallery2/lib/adodb/drivers/adodb-mysql.inc.php on line 348
serverhostname: Lost connection to MySQL server during query

someone can help me please?
Thanks a lot...

Silvio.

---

### Post by Georges on 2007-01-05
same problem here.

It has all to do with mysql and database setup which is simply silently ignored by all the "how to install gallery2" guides out there. I find this so damn silly.

So I will now have to look into:

- how to configure mysql
- how to setup phpmyadmin
- how to create a database with phpmyadmin

and various other crap, instead that the gallery2 guides should be fully featured "do like that and it works". Funny is, the guide talks about apt-get install mysql, so why not about the rest concerning the database?

So here we are, 6 months later and it's still the same "user got stranded on the cliff" situation.

Georges

---

### Post by Georges on 2007-01-05
so digging through the detailed install guide here is what is missing:

you have to replace [COLOR="Red"]*gallery2*[/COLOR] by the database name you want, if you only use one install you can leave it. You have to replace *username* and *password* by the data you give in step 5 as [COLOR="Green"]*DB Username*[/COLOR] and [COLOR="Navy"]*DB Password*[/COLOR] of the gallery2 installation. Don't try to use special characters in the database name, it got me stuck somewhere.
```

sudo mysqladmin -uroot create [COLOR="Red"]gallery2[/COLOR]
sudo mysql [COLOR="Red"]gallery2[/COLOR] -uroot -e"GRANT ALL ON [COLOR="Red"]gallery2[/COLOR].* TO [COLOR="Green"]username[/COLOR]@localhost IDENTIFIED BY '[COLOR="Navy"]password[/COLOR]'"

```

no need for phpmyadmin.

---

