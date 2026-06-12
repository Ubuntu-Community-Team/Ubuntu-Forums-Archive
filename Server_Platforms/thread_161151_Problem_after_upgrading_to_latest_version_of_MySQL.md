---
title: "Problem after upgrading to latest version of MySQL"
date: 2006-04-16
forum: Server Platforms
---

### Post by scratched on 2006-04-16
I just upgraded from MySQL4.1 to MySQL 5.0 using [Dudus' HOWTO]("http://www.ubuntuforums.org/showthread.php?t=93725"). 

After I upgraded, I was no longer able to connect to MySQL. Whenever I try I get this error
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

```

I've tried opening port 3306 through firestarter but that didn't help any.

Could anyone give me any idea as to what I need to do to fix the problem?

I'm new to linux so this has me totally confused:-k

---

### Post by LordHunter317 on 2006-04-16
It's because you're likely still using hte older clients and it's expecting the socket in a different place.

Alternatively, you're still using a wrong/invalid my.cnf

This is why I explictly said people shouldn't use that unless they know exactly what they're doing.  

If I were you, I'd back out the changes the best you can and pin in dapper and install mysql-5.0 from there, if you need it.

---

### Post by scratched on 2006-04-16
Oh well...

I'm using the database strictly for personal use to teach myself the differences between Oracle and MySQL since I was taught in Oracle but plan on using a MySQL database in the near future, so I'm not too concerned about the damage I did.

I could uninstall MySQL completely if I have to. The main reason I want to use MySQL5 is because of it's support for views.

If needed absolutely, I could even re-install ubuntu since I'm only using ubuntu to learn linux with. Linux is not yet my primary OS.

---

### Post by LordHunter317 on 2006-04-16
What do you plan to use MySQL for?  If it's custom development, I would never use MySQL anything unless the choice was strictly out of my hands.

---

### Post by scratched on 2006-04-16
At the moment I have a group project for school that I'm working on for a database class and the group member who is hosting the site we're running the project off of has a MySQL server so I need to be able to test out everything before we upload it to the actual server.

I'm also going to using it in the future for a website I've recently started working on (I'm not hosting it). The web host I'm using has MySQL server so I wanted to know the quirks of MySQL before I really got started.

---

