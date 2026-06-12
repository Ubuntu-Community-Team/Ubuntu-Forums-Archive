---
title: "PHPMyAdmin: what is the &quot;MySQL application password for phpmyadmin&quot;?"
date: 2015-02-17
forum: Server Platforms
---

### Post by stupidquestion on 2015-02-17
During PHPMyAdmin installation, it first asks for the existing MySQL root password, but then it asks for a second password called "MySQL application password for phpmyadmin". The text provided was "please provide a password for phpmyadmin to register with the database server. If left blank, a random password will be generated".

What is this password used for? I noticed I can log in from the phpmyadmin web homepage without using this second password.

---

### Post by nerdtron on 2015-02-18
not using phpmyadmin but you can login to the mysql via command line,
then see it the phpmyadmin already has a user
```

mysql> use mysql;
mysql> select user,host,password from user;

```

If so, then you just set a new password:
```
mysql> SET PASSWORD FOR 'phpmyadmin'@'localhost' = PASSWORD('passxxx'); 
```

---

### Post by stupidquestion on 2015-02-18
thanks, I realized that "phpmyadmin" is a user in the mysql database.

---

