---
title: "Troubles installing WordPress"
date: 2005-10-19
forum: Server Platforms
---

### Post by woland on 2005-10-19
For starters I'm still a newbie in linux.
I'm trying to make my own blog on my computer with WordPress but couldn't get it work. I've been using apache2 for some time and installed MySQL and PHP4 for  WordPress, who both seem to work. 
When I follow the instalation guide I get the following error:
```
Your PHP installation appears to be missing the 
MySQL which is required for WordPress.
```

---

### Post by Beernut on 2005-10-19
Did you create a MySQL user for wordpress?

[http://codex.wordpress.org/Installing_WordPress#Using_the_MySQL_Client](http://codex.wordpress.org/Installing_WordPress#Using_the_MySQL_Client)

---

### Post by majikstreet on 2005-10-19
I would recommend installing PHPMyAdmin- it really makes life easier for you. I don't remember how I did it though. I think I got the tar.gz and put it in my /var/www directory and edited some config files to let you login as the mysql users themselves.

Then you follow [http://codex.wordpress.org/Installing_WordPress#Using_phpMyAdmin](http://codex.wordpress.org/Installing_WordPress#Using_phpMyAdmin)

---

### Post by jg123 on 2005-10-20
Did you install this package --> php4-mysql
It should connect php to mysql.

---

