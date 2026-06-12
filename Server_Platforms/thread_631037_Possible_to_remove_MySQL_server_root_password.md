---
title: "Possible to remove MySQL server root password?"
date: 2007-12-04
forum: Server Platforms
---

### Post by Scooter7 on 2007-12-04
Hi,

For a while now, I've been running my MySQL server (installed with LAMP - I'm running Ubuntu 7.04 Server Edition) without a password.   I realized this when I updated the server, so I ran this command to create a password:

```
sudo /etc/init.d/mysql reset-password
```

Now, though, a couple forums I have installed in the database can't connect to the server because they're configured to work without a password.   I also can't use PHPMyAdmin, because I get this error when I load up the page:

> #1045 - Access denied for user 'root'@'localhost' (using password: NO)

Is there a way to remove the password?   I've tried running the command again, and just hitting enter when I'm prompted for the new password, but this didn't seem to work.

---

### Post by primski on 2007-12-04
Yes, indeed it can be done.

go to mysql prompt with
```

mysql -u root -p<password>

```

then, use 'mysql' database
```

use mysql;

```

select, which user to change
```

select Host, User, Password from user ;

```

and change the desired user 
```

update user set password = '' where user = 'root' and host = 'localhost';

```
or equivalent.

Good luck,

pr

---

