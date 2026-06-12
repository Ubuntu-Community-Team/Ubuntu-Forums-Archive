---
title: "libmysqlclient upgrade"
date: 2010-01-09
forum: Server Platforms
---

### Post by cavh on 2010-01-09
Good day all,

I installed LAMP using tasksel and have been happy with it, thanks to those who made such an installation so painless! I've installed LAMP on Windows and other *nix variants over the years and this was by far the easiest. Thank you.

Now I needed to upgrade the mysql server due to a bug in 5.0 to do with parentheses in enum. The server is now at 5.1.31-1ubuntu2. However, phpmyadmin is showing a warning to the effect that 'Your PHP MySQL library version 5.0.75 differs from your MySQL server version 5.1.31. This may cause unpredictable behavior.' 

Using Synaptic I see that I have two libmysqlclient versions installed - *libmysqlclient15off* and *libmysqlclient16 (5.1.31-1ubuntu2)*. It seems I clear I should be using *libmysqlclient16* to get rid of the phpmyadmin warning. However, when I mark *libmysqlclient15off* for removal, Synaptic warns me that the following will also be removed, which worries me: 

apache2, phpmyadmin, php5-mysql etc. etc.

How can I use *libmysqlclient16* without trashing the LAMP installation?

---

### Post by cavh on 2010-01-10
bump

---

### Post by stlsaint on 2010-01-10
have you tried just updating:

```
 sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by gbusse on 2010-04-07
I too would like to find a solution for this problem. I installed Zend Server CE 5 and with either the bundled phpMyAdmin or Ubuntu's version I get the following error in phpMyAdmin.

Your PHP MySQL library version 5.0.83 differs from your MySQL server version 5.1.37

Thanks in advance to anyone who can shed some light on this?

There are no upgrades or dist-upgrades available either!

FYI, running a fully updated install of Karmic along with Zend Server CE 5.

Thanks,
Gord

---

### Post by gbusse on 2010-04-07
Well I appear to have solved this problem. At least for me anyways. All I did was completely uninstalled MySQL 5.1.37ubuntu5.1 (server/client/core) then installed MySQL 5.1.30really5.0.83-0ubuntu3 (server/client/core). I also had to reinstall phpMyAdmin as well for some reason but after that everything worked fine as the reported PHP MySQL client version and the server version are both the same now.

Hopefully this problem won't happen in Lucid and we can use MySQL 5.1+.

Gord

---

