---
title: "MySQL changing password"
date: 2008-10-14
forum: Server Platforms
---

### Post by satimis on 2008-10-14
Hi folks,


I have run following command;```

GRANT SELECT, INSERT, UPDATE, DELETE ON mail.* 
TO 'mail_admin'@'localhost' IDENTIFIED BY 'mail_admin_password';

```


Now I need changing password.


Whether run following command;```

mysql> UPDATE mysql.user SET Password = PASSWORD('new_password')
    ->     WHERE User = 'mail_admin@localhost';
mysql> FLUSH PRIVILEGES;

```

TIA


B.R.
satimis

---

