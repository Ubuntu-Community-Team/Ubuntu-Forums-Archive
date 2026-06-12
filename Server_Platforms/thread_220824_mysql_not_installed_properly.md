---
title: "mysql not installed properly?"
date: 2006-07-22
forum: Server Platforms
---

### Post by GlurG on 2006-07-22
Hi

I've installed Apache 2, PHP5 and Mysql 5 server using the Synaptic package manager. The problem is that I get the following error trying to connect to my mysql through php:
```

Fatal error: Call to undefined function mysql_connect() in /var/www/index.php on line 3

```
I guess it has basically to do with my mysql.so extension not being setup properly. But I haven't found the extension directory, so I can't verify that I even have a mysql.so file...

btw, I'm on a Ubuntu 6.06 box.

---

### Post by dermotti on 2006-07-22
Does phpinfo come up properly and show mysql installed?

make a file called phpinfo.php with the contents:

<? phpinfo() ?>

and pull it up in your browser

[http://127.0.0.1/phpinfo.php](http://127.0.0.1/phpinfo.php)

---

### Post by GlurG on 2006-07-22
According to phpinfo(), mysql does not seem to be installed at all...I couldn't find anything regarding mysql in phpinfo.
Is this a configuration issue or do I have to reinstall mysql altogether?

---

### Post by brendon on 2006-07-22
Have you intalled php4-mysql?

It provides access to mysql from php.

---

### Post by lamego on 2006-07-22
The ability to connect to mysql from php is not provided by MySQL itself, it is provided by the php module for mysql.
If you are using php5 you need to install it with:
```
sudo apt-get install php5-mysql
```

---

### Post by GlurG on 2006-07-23
I installed php5-mysql and restarted Apache. But I still can't find anything about mysql in phpinfo(). I have the mysql-extension enabled in the php.ini.
```

extension=mysql.so

```
Thing is that I don't think I even have a file called mysql.so (or php_mysql.so)...did a search and it came up with nothing.
Seems like I've missed to install yet another package(?)

---

