---
title: "MySQL php access denied for all accounts, yet PHPMyAdmin works fine?"
date: 2014-02-17
forum: Server Platforms
---

### Post by ian33 on 2014-02-17
I have just set up an Ubuntu web server (I'm new to Linux) and I have finally got round to setting my website up. However, I cannot connect to the local database using either the IP address or 'localhost'. PHPMyAdmin works absolutely fine, but I can't connect to mysql even when I use the same access details as PHPMyAdmin.

I am connecting with the following PHP code (which worked fine on my laptop and on my other server):

```
mysqli_connect($server, $username, $password, $database);
```

I have created a brand new account and granted full permissions to it, but with no luck. 

If I use the IP address to connect, I get the following error:

```
Not connected : Can't connect to MySQL server on '(ip address)' (111)
```

If I use 'localhost', I get the following error:

```
Not connected : Access denied for user 'newuser'@'localhost' (using password: YES)
```

I am 100% sure the password is correct and, seeing as PHPMyAdmin works fine, I am sure the MySQL service is running. If I run mysql in safe mode, it connects absolutely fine and everything works well.

I have apache and mysql on the same machine.

Any help would be appreciated!

---

