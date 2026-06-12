---
title: "How do I change the MySQL collation server?"
date: 2007-08-30
forum: Server Platforms
---

### Post by jdbg on 2007-08-30
Hi guys,

I want to ask how do I change the MySql collation server and collation database parameters? These are global, but through the phpmyadmin I can't change them.

10x in advance

---

### Post by jdbg on 2007-09-10
anyone please?

---

### Post by koenn on 2007-09-10
If this : [http://www.unitedforums.co.uk/vb/website-development-scripting/8329-mysql-collation-use.html#post59603](http://www.unitedforums.co.uk/vb/website-development-scripting/8329-mysql-collation-use.html#post59603)
is what you're looking for, then it's something you change by sending sql statements to your db / dbms. 
You either have a suitable frontend that lets you do interactive SQL, or you use the commandline tool that comes with MySQL, probably something like
```

 mysql -u root -p mysql
PASSWORD:

mysql> [do sql stuff here];

mysql> quit;

```

---

