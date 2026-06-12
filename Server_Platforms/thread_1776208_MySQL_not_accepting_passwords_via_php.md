---
title: "MySQL not accepting passwords via php"
date: 2011-06-05
forum: Server Platforms
---

### Post by DanHorniblow on 2011-06-05
Hi, I have just set my self up a new LAMP server running php and mysql.

I get the following error when trying to acces mysql databases through php

```
Could not connect: Access denied for user 'danhorni'@'localhost' (using password: NO)
```

I am using a password

I can login fine through phpmyadmin

Any ideas?

---

### Post by Baumbart on 2011-06-06
"Using password No" means you didn't give a password_ in your query_ although the mysql-db expects one.

Is everything alright with the php-syntax?
For example if you use something like $strDBPass, is that variable actually set in the script-context, isn't it empty? 
It's usually stuff like this when I get that error.

---

