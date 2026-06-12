---
title: "Needing MySQL Users"
date: 2013-09-06
forum: Server Platforms
---

### Post by athf-president on 2013-09-06
Ok, a bit of a story:

I was changing information for my mediawiki, and I changed my username and password inside my LocalSettings.php file. When I updated the wiki, it is no longer accessible. The errors I am getting are related to MySQL. I do not know the login for the root MySQL account on my server. I want to get the user name and password associated with mysql back so I can at least restore my wiki. Here is what I know so far:

When I first try to access the wiki, i get

(Can't contact the database server: Access denied for user 'root'@'localhost' (using password: YES) (localhost))

I ran mysqld_safe --skip-grant-tables &

130906 19:38:55 mysqld_safe --skip-grant-tables &

I tried running mysqld stop, it runs, but then I try rerunning the command and it still says it is running. My end goal is just to be able to view the original user name and password so I can restore my wiki

I am dead in the water at this point and I have no idea how to proceed

Thank you very much for your time

---

### Post by CharlesA on 2013-09-07
Where is this wiki hosted? As a general rule of thumb, you shouldn't need to use the root user to update the wiki software. If you do need to use a different user, it is a good idea to comment out the connection information so you don't lose it.

As far as I know the passwords in the database are encrypted, but you should be able to see which users exist by running:

```
SELECT User FROM mysql.user;
```

After you log in. If you don't know the root password for mysql, you can reset it, but if you aren't the one administering the server, it would be best to check with them before doing anything.

---

### Post by M!K3_$ on 2013-09-08
If you have root access to mysql you can find and change the password for your wiki user:
[http://www.cyberciti.biz/faq/mysql-change-user-password/](http://www.cyberciti.biz/faq/mysql-change-user-password/)

If you don't have the root mysql password you can reset it:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

