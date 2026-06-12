---
title: "getting MySQL to work with Apache2"
date: 2005-11-30
forum: Server Platforms
---

### Post by Aven on 2005-11-30
Alright..

my MySQL server is up and running with other databases...

But how can I make Apache2 recognize MySQL?

Would I need the libapache2-mod-auth-mysql module?

If so, I installed it but it does not load. (PHP4, cgi, etc. automaticlly loaded themselves after installtion)

how can I load it? and is it a requirement for the MySQL server to work with Apache2?

thanks

---

### Post by LordHunter317 on 2005-11-30
You only need that if you want to do HTTP authentication with a MySQL database.

Apache usually doesn't need to be aware of your database(s), PHP does.  Install php4-mysql if you're missing MySQL support in php4.

---

### Post by Aven on 2005-11-30
I have php4-mysql, yes... but it still won't work :\

anyone know what the problem could be?

help is really apprectiated!


thanks

---

### Post by Aven on 2005-11-30
Ok, according to Synaptic:
```

/.
/usr
/usr/lib
/usr/lib/php4
/usr/lib/php4/20050606
/usr/lib/php4/20050606/mysql.so
/usr/share
/usr/share/doc
/usr/share/doc/php4-mysql

```

Those are the directories it puts the mysql module in... non are apache2-related.

so, how would I load the mysql.so module from apache2?

thanks!

---

### Post by Aven on 2005-11-30
Ah, it works now...

I removed libapache2-mod-php4, php4 and php4-mysql and installed

libapache2-mod-php5, php5, and php5-mysql instead.

woohoo php5!

---

### Post by slempl on 2005-12-19
Yes....    but is it possible to use old php4 functions in pfp5?.....  because my job mates and me use php4 and we have made templeates wich i could not use if i install php5  i'm the only one running ubuntu machine...  and so on....

Should i reinstall phpmyadmin?

---

