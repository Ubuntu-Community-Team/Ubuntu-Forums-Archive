---
title: "MySQL - about update password"
date: 2008-10-21
forum: Server Platforms
---

### Post by satimis on 2008-10-21
Hi folks,


I ran;

```

mysql> GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* TO 'mail_admin'@'localhost' IDENTIFIED BY 'oldpassword';

```
creating password


Now I need changing its password whether to run;
```

mysql> UPDATE user SET password=PASSWORD('newpassword') WHERE user="'mail_admin'@'localhost'";

```


Then where to put mail.* ?   It is NOT a database.


TIA


B.R.
satimis

---

### Post by StickyStyle on 2008-10-23
I'm not exactly sure why you are questioning where to put mail.*, you have already assigned the user/host permissions in the first command, it's not needed again when you set the password.

Also, BTW - doing an update on the mysql db directly is not the recommended method.  Instead do...
```

SET PASSWORD FOR 'mail_admin'@'localhost' = PASSWORD('newpassword');

```

---

### Post by satimis on 2008-10-24
> **StickyStyle said:**
> I'm not exactly sure why you are questioning where to put mail.*, you have already assigned the user/host permissions in the first command, it's not needed again when you set the password.

Also, BTW - doing an update on the mysql db directly is not the recommended method.  Instead do...
```

SET PASSWORD FOR 'mail_admin'@'localhost' = PASSWORD('newpassword');

```
Hi StickyStyle,


Thanks for your advice.  If I understand it correctly.  To change password just run;

# mysql -u root -p

mysql> SET PASSWORD FOR 'mail_admin'@'localhost' = PASSWORD('newpassword');

mysql> FLUSH PRIVILEGES;

mysql> quit;


B.R.
satimis

---

### Post by StickyStyle on 2008-10-24
FLUSH PRIVILEGES is not need when you use the SET PASSWORD function, only when you update the mysql database directly as you where doing initially.  Although calling FLUSH PRIVILEGES as you have done here is not going to affect anything in a negative way.

Otherwise, yes your understanding correctly.

---

### Post by satimis on 2008-10-24
> **StickyStyle said:**
> FLUSH PRIVILEGES is not need when you use the SET PASSWORD function, only when you update the mysql database directly as you where doing initially.  Although calling FLUSH PRIVILEGES as you have done here is not going to affect anything in a negative way.

Otherwise, yes your understanding correctly.
Thanks


satimis

---

