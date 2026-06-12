---
title: "phpMyAdmin"
date: 2006-07-01
forum: Server Platforms
---

### Post by rowanparker on 2006-07-01
Hello,
I just installed apache2, php5, mysql and phpmyadmin for testing my websites.
I could get onto phpmyadmin fine when it was installed then I restarted and now i get this message:> Error
The configuration file now needs a secret passphrase (blowfish_secret).
It used to work fine, i don't remember changing anything.

How can I get it to work again?

Thanks, Rowan.

---

### Post by saaz on 2006-07-01
Open up your config.inc.php file in the phpMyAdmin directory and look for this line:

```

$cfg['blowfish_secret'] = '';

```

Give it a password. It doesn't really matter what you set it too since it won't ask you for it. For example:

```

$cfg['blowfish_secret'] = 'foo';

```

HTH

---

### Post by rowanparker on 2006-07-01
I changed that to 'foo' in every config file I could find.
Still displays that error.

---

### Post by az on 2006-07-01
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you get blowfish_secret error: Choose and set a phrase for cryptography in the file /etc/phpmyadmin/blowfish_secret.inc.php and copy the line (not the php tags) into the file /etc/phpmyadmin/config.inc.php or you will receive an error.

---

### Post by rowanparker on 2006-07-02
Works great, thank you.

---

### Post by Wangsta on 2008-01-29
Wait, how do you even start PHP MyAdmin?
I installed it, but there's not any command that runs it or anything. The same goes with Mysqladmin.
How do I get them started???

---

### Post by rowanparker on 2008-01-29
> **Wangsta said:**
> Wait, how do you even start PHP MyAdmin?
I installed it, but there's not any command that runs it or anything. The same goes with Mysqladmin.
How do I get them started???
[http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

+ Dude, this topic was like at least 18 months old!

---

### Post by Wangsta on 2008-01-30
thanks alot!
but I forgot my password for my mysql database.
is there any way I can get it back?

---

### Post by Ainab on 2008-01-31
did you change during installation? if you did not then it is root.

---

### Post by Wangsta on 2008-01-31
this is what I got:
```

server@server:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```
I DID make a 'mysql' user, though whatever that means.

I also tried using this:```

server@server:~$ sudo /etc/init.d/mysql stop
[sudo] password for server:
 * Stopping MySQL database server mysqld                                 [ OK ] 
server@server:~$ /usr/bin/mysqld --skip-grant-tables --user=root
bash: /usr/bin/mysqld: No such file or directory
server@server:~$ 


```

Do I just have to totally remove mysql?? Isn't there another way?

---

### Post by califman831 on 2008-02-08
ditto for me, i would love to explore mysql but haven not gotten over the password  fence

---

