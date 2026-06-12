---
title: "Mysql"
date: 2009-01-17
forum: Server Platforms
---

### Post by xnerdx on 2009-01-17
Okay, I have mysql installed like this:
```

sudo apt-get install mysql-server mysql-client libmysqlclient15-dev

```
The problem is that now that I have it installed I can't figure out how to run my database. I need to execute a couple .sql scripts into the server on my local host. When I try to do anything it denies me completely. I have tried to access it with MySQL Navigator 1.4, I log in as mysql on local host and it shows me a database information_schema. I am lost after that, does anyone know how I can just install it over again or something so I can set it so it is a root username and I can set my own password, any help would be wonderful.

---

### Post by jonabyte on 2009-01-18
you may need to set the root password first, if you haven't already:

```
mysqladmin -u root password NEWPASSWORD
```

---

### Post by Bachstelze on 2009-01-18
The debconf script for MySQL does prompt for a root password. If you have missed that, you should be able to do it again with

```
sudo dpkg-reconfigure mysql-server
```

Then you need to create a database and execute your script, using whatever you normally use.

---

### Post by xnerdx on 2009-01-18
Okay, I did this one:
```
$ sudo mysqladmin -u root password ascent
[sudo] password for $: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

When I ran this:
```
$ sudo dpkg-reconfigure mysql-server
$ sudo dpkg-reconfigure mysql-server

```
Both times it just went to the next line and nothing opened. Afterwards I tried to run the mysqladmin code and it gave me the same error.

---

### Post by xnerdx on 2009-01-18
Problem resolved, I went synaptic and search mysql, completely removed everything installed. Then I ran the original sudo apt-get code I said I had to run, I did that and it prompt me for a root password. Thanks for you attempts to help

---

