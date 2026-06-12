---
title: "Which table structure is MySQL using"
date: 2012-06-11
forum: Server Platforms
---

### Post by larka06 on 2012-06-11
I just found out that MySQL is going to start using MYISAM instead of InooDB. This is a different database structure. My question is does anybody know what database structure Ubuntu is using and, how do I tell which it is using?  I am doing a book right now that uses Inoob which will not work on 12.04 at several things. I have put CentOS 6.2 in a virtual machine and it works perfectly. I do not wish to switch but the database is essential at this time.
Help

---

### Post by Habitual on 2012-06-11
[http://dev.mysql.com/doc/refman/5.5/en/innodb-default-se.html](http://dev.mysql.com/doc/refman/5.5/en/innodb-default-se.html)

```

mysql -e "SHOW VARIABLES LIKE 'have_innodb'"

```

---

### Post by larka06 on 2012-06-11
Thanks for the link. I know have it straight what is what.
Thanks

---

### Post by Habitual on 2012-06-12
Glad it worked out.

---

