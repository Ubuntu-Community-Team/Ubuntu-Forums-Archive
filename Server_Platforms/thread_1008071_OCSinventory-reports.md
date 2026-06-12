---
title: "OCSinventory-reports"
date: 2008-12-11
forum: Server Platforms
---

### Post by puesco on 2008-12-11
Hi,

I installed an Ubuntu 8.10 server (LAMP) and want to run OCS-inventory on it. I installed it using apt (package: OCSinventory-reports). Calling localhost on a browser shows "It works!" so Apache is up and running. Calling localhost/ocsreports gets the initial page which calls "install.php".(Screenshot1)
And here comes my problem: "install.php" asks for a user/password which I have not set anywhere and I have tried all accounts which have been created (local user, root, mysql-root,...) (Screenshot2)

Since this seems to be a congiguration matter with apache, can anyone tell me, where I can adjust/fix this? Or does anyone know, which user/password is asked for in this case?
BTW: Installing OCS from source does not have this problems.

Thanks a lot!
Kai

---

### Post by bluefrog on 2008-12-11
isn't it asking for mysql root password which you have set up when installing LAMP?

---

### Post by BOK on 2009-02-10
See [https://bugs.launchpad.net/ubuntu/+source/ocsinventory-server/+bug/238111](https://bugs.launchpad.net/ubuntu/+source/ocsinventory-server/+bug/238111)

---

### Post by Saghaulor on 2009-11-20
Okay, so I was able to authenticate, and then build the database.

Now, when I try to go to [http://myserver/ocsreports/index.php](http://myserver/ocsreports/index.php)

I am asked to log in. I try to log in with all users listed in the ocsweb database, and I receive an error that > User not registered


I'm confused. Any help would be appreciated.

Edit:

user: admin
pw: admin

---

