---
title: "MySQL Server 5.1 Access Denied"
date: 2011-07-29
forum: Server Platforms
---

### Post by dmubu on 2011-07-29
I have just installed the LAMP stack for Ubuntu.

When I run:

```

mysql -u root -p

```

or

```

mysql -h localhost -u root -p

```

I receive:

```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

What should I do?  Since I cannot set up the database, I cannot install phpMyAdmin correctly.

Thank you!

---

### Post by karlson on 2011-07-29
> **dmubu said:**
> I have just installed the LAMP stack for Ubuntu.

When I run:

```

mysql -u root -p

```

or

```

mysql -h localhost -u root -p

```

I receive:

```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

What should I do?  Since I cannot set up the database, I cannot install phpMyAdmin correctly.

Thank you!

Do you type in the password?  Did you set it when you installed the package?

---

### Post by fdrake on 2011-07-30
reinstall mysql, it will ask you to create a new password

```
sudo apt-get install mysql-server
```

---

### Post by dmubu on 2011-07-30
Thanks for the reply.

I re-installed, but still no luck:

```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

Should I edit the my.cnf file?  Is there anything else I can do?  Currently, I am striking out...

---

### Post by fdrake on 2011-07-30
did you try [this link]("http://www.cyberciti.biz/tips/recover-mysql-root-password.html")?

---

### Post by dmubu on 2011-07-30
That seemed to work...thank you!

---

