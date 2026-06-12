---
title: "Can't connect to mysql from php"
date: 2006-09-24
forum: Server Platforms
---

### Post by gfd on 2006-09-24
Hello,

When I try to connect to MySQL from PHP I get the following error:
```
mysql_connect(): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'
```

MySQL is running fine, and I can connect to it from the command line.
If I do a "mysqladmin version" I can see that the socket file being used is actually /tmp/mysql.sock and not '/var/run/mysqld/mysqld.sock'.

I have checked the /etc/php4/apache2/php.ini and I can't see anything wrong.

I have also gone through the Ubuntu [ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") guide and everything seems right.

Does anybody know what might be causing this?

Thank you

---

### Post by kidders on 2006-09-24
You could try specifying the socket location manually. This can be done in php.ini if you like ... I think the setting is called "mysql.default_socket".

If you don't tell PHP specifically what to do, it tries to guess things ... which doesn't always work!

---

### Post by gfd on 2006-09-25
> **kidders said:**
> You could try specifying the socket location manually. This can be done in php.ini if you like ... I think the setting is called "mysql.default_socket".
Thanks kidders, I tried that but I still get the same error.
I even tried specifying the mysql.default_user too, but that didn't help either.

Any other ideas?

Where else could this path be specified and why is it looking for mysqld.sock and not mysql.sock?

---

### Post by kidders on 2006-09-25
In the PHP script itself.

Bear in mind that you may have to restart apache for php.ini changes to take effect. (Just checking.)

---

### Post by gfd on 2006-09-25
> **kidders said:**
> restart apache for php.ini changes to take effect
Did that...
> **kidders said:**
> In the PHP script itself.

The script just uses [PHP]mysql_connect('localhost', $user, $pass)[/PHP]

---

### Post by kidders on 2006-09-25
Okay, that's ... ehhh ... weird! There are two things you can do at this point.

**Thing 1**
Try to make the problem go away with **sudo ln -s /tmp/mysql.sock /var/run/mysqld/mysqld.sock** It's a bit hacky, but it should cooperate for you. A better solution would be to have MySQL actually move the socket. Find the section called "mysqld" (the 'd' is very important) in /etc/mysql/my.cnf, and add (or change) **socket          = /var/run/mysqld/mysqld.sock** Then, restart MySQL.

**Thing 2**
Try harder to find the problem. I've thought about it for a few minutes and I'm out of useful suggestions though :-( One possibility is that you may have installed more than one version of PHP ... PHP4 and PHP5, say, or maybe CGI and apache module versions. Basically, it's possible you're inadvertently editing the wrong php.ini. Is there any way that might be so?

I hope one of these choices proves useful!

---

### Post by gfd on 2006-09-25
> **kidders said:**
> **sudo ln -s /tmp/mysql.sock /var/run/mysqld/mysqld.sock** It's a bit hacky, but it should cooperate for you.
That did it!!
I do understand that this is a bit hacky, but, since it works, I'll use it as a temporary solution for now because I can't really afford to spend any more time on this today.
I will definetely look into though at a more appropriate time.

Your help is greatly appreciated, kidders. Thank you very much.

---

