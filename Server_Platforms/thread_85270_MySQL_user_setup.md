---
title: "MySQL user setup"
date: 2005-11-02
forum: Server Platforms
---

### Post by Lapeth on 2005-11-02
When installing the MySQL server from the repos and setting it up, I constantly run into the problem that I can't log into the server as root. It gives me the following error:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Well, that sucks.

I'm using the guide [here]("http://dev.mysql.com/doc/refman/5.0/en/unix-post-installation.html"), but no matter what I try, it still refuses to let the root user log in. As far as I can tell, the script "mysql_install_db" will set up the privileges, and a command like "mysqladmin -u root password '8888'" will give root the password 8888. This last command, among others, yields the above mentioned error.

---

### Post by dbee on 2005-11-02
It looks like you've given root a password, but then you are trying to login without using one (if I understand you correctly).

try 
```

mysql -u root -p

```

then enter the password 8888 on the return line

also try looking in your user.MYD file to get a reasonable view of your user-password setup
```

strings /var/lib/mysql/mysql/user.MYD

```

---

### Post by Lapeth on 2005-11-02
Worked like a charm. Figured out that I need to supply the -p option every time, since it's not there by default. Sorry for being ignorant, but I haven't used MySQL before.

---

### Post by dbee on 2005-11-04
No-one who asks a question is ignorant. 
Ignorance is reserved exclusively for those who don't ask.

---

