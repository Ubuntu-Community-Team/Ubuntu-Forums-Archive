---
title: "Cannot set password for MySQL server in LAMP stack"
date: 2011-07-30
forum: Server Platforms
---

### Post by dmubu on 2011-07-30
I was having trouble getting my MySQL server.  I kept receiving "ACCESS DENIED" messages until I did the following:

```

mysqld_safe --skip-grant-tables &

```

I then tried to set a password by entering:

```

update user set password=PASSWORD("mypassword") where User='root';

```

and receive this error message:
```

ERROR 1046 (3D000): No database selected


```

So, I can now access MySQL  server through the terminal, but I never get prompted for a password.  How can I fix this?

---

### Post by wojox on 2011-07-30
```

mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit

```

Like that. You told it what DB to use?

---

