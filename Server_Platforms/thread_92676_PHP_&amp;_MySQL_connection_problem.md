---
title: "PHP &amp; MySQL connection problem"
date: 2005-11-20
forum: Server Platforms
---

### Post by MarkTheDaemon on 2005-11-20
Hey

First of all i think ubuntu is great! What i want to do is set up a webserver. I have apache, php and mysql installed but the php and mysql won't "talk" to each other :confused: 

I've got experience in installing webservers on windows but i decided to make the change to linux, so make things simple :smile: 


Thanks

Mark

---

### Post by bmichel on 2005-11-20
Apache MySql and PHP are working very well together on Ubuntu and most of the configuration is not so different from Windows version.

Perhaps you should start by searching on Google and you''ll find plenty of information how to configure a LAMP stack whatever the linux distrib.

Also look at this for Ubuntu : [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

You've made the good move.

---

### Post by Novastorm on 2005-11-20
Assuming you installed apache, php and mysql using apt-get. The only thing i had to change to get php talking to mysql was i needed to load the mysql module in php. You can do this by editing /etc/php5/apache2/php.ini and finding the line like this

```
; extension=mysql.so
```

to

```
extension=mysql.so
```
note: just remove the semi-colon

Then restart apache,

```
sudo /etc/init.d/apache2 restart
```

---

### Post by tsumi on 2005-11-22
[QUOTE=bmichel]Apache MySql and PHP are working very well together on Ubuntu and most of the configuration is not so different from Windows version.

Perhaps you should start by searching on Google and you''ll find plenty of information how to configure a LAMP stack whatever the linux distrib.

Also look at this for Ubuntu : [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

You've made the good move.[/QUOTE]

-- THANK YOU!! (for the link)

---

