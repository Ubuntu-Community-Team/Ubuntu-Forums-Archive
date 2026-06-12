---
title: "Uninstalling MySQL and phpmyadmin"
date: 2011-02-09
forum: Server Platforms
---

### Post by tbobker on 2011-02-09
The original issue started when i couldnt login to phpmyadmin. I noticed an error when installing it and when trying to login, my credentials that I supplied upon install failed. 

After ages of messing around trying to reset I decided to try and uninstall phpmyadmin and MySQL and start again. 

This has produced more issues as I uninstalled MySQL first and phpmyadmin asks for credentials that are in a database, which I have already deleted. This causes major issues trying to uninstall it. 

Anyway, I have used all these commands:

sudo apt-get remove phpmyadmin
sudo apt-get remove mysql-server
sudo apt-get remove mysql-common

Now I am trying to install everything again but having erros. This is what I have so far:

```

root@ks358041:/var/lib/php5# sudo apt-get install mysql-server-5.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  mysql-server-5.1: Depends: mysql-client-5.1 (>= 5.1.41-3ubuntu12.9) but it is not going to be installed
                    Depends: libmysqlclient16 (>= 5.1.21-1) but it is not going to be installed
                    Depends: mysql-server-core-5.1 (>= 5.1.41-3ubuntu12.9) but it is not going to be installed
                    PreDepends: mysql-common (>= 5.1.41-3ubuntu12.9) but it is not going to be installed
  phpmyadmin: Depends: php5-mysql but it is not going to be installed or
                       php5-mysqli but it is not installable
              Recommends: mysql-client
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ks358041:/var/lib/php5# 

```

Any help really appreciated.

---

### Post by cariboo on 2011-02-09
Apt-get remove only removes the packages, and none of the configuration files. To completely remove a package use:

```
sudo apt-get purge mysql-server
```

the above command will remove everything. Make sure the service is stopped before purging it.

---

