---
title: "About mysql administrator"
date: 2006-11-23
forum: Server Platforms
---

### Post by satimis on 2006-11-23
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
xfce4 desktop

$ sudo apt-cache search mysql | grep admin```

dpsyco-mysql - Automate administration of access to mysql
eskuel - A pretty PHP administration tool for MySQL databases
kmysqladmin - Kde graphical frontend for mysql servers
mysql-admin - GUI tool for intuitive MySQL administration
mysql-admin-common - Architecture independent files for MySQL Administrator
phpmyadmin - set of PHP-scripts to administrate MySQL over the WWW
tora - A graphical toolkit for database developers and administrators
courier-webadmin - Courier Mail Server - Web-based administration frontend
```
Are "mysql-admin" and "mysql-admin-common" MySQL Administrator?

$ which mysql-admin
$ which mysql-admin-common
Both no printout.

$ sudo find / -name mysql-admin
also no printout

Please advise how to start MySQL Administrator?  TIA


B.R.
satimis

---

### Post by adwait on 2006-11-23
```
mysql-admin
```

---

### Post by satimis on 2006-11-23
Hi adwait,

Tks for your advice.

> ```
mysql-admin
```

I tried before.

$ mysql-admin
bash: mysql-admin: command not found
$ ./mysql-admin
bash: ./mysql-admin: No such file or directory

What is the correct name of this package on repository?  

What other commands other than "apt-cache search package" can I run checking whether a package has been installed?

TIA


B.R.
satimis

---

### Post by adwait on 2006-11-23
Ooh, I thought you already had it installed and wanted to run it. To install it, you have to use
```
sudo apt-get install mysql-admin
```

---

### Post by satimis on 2006-11-23
Hi adwait,

I got "mysql-admin" installed.  Tks.


On Ubuntu what is the command for checking whether a package has been installed?

TIA


B.R.
satimis

---

### Post by adwait on 2006-11-23
```
dpkg -l <packagname>
```

---

### Post by satimis on 2006-11-23
> **adwait said:**
> ```
dpkg -l <packagname>
```
Noted with tks.


B.R.
satimis

---

