---
title: "install LAMP ontop of desktop?"
date: 2006-11-27
forum: Server Platforms
---

### Post by Darth_tater on 2006-11-27
i built a PC out of some scrap components i had lying arround and i have already installed 6.10 w/ gnome.  is there an easy way to install the LAMP server ontop of it?  (by easy i mean the same way you install the desktop "sudo apt-get install ubuntu-desktop"


thanks!

---

### Post by cilynx on 2006-11-27
```
sudo apt-get install apache2 mysql-server
```

Linux (duh) and Perl / PHP should already be around...

---

### Post by az on 2006-11-27
Actually, the packages are

apache2 php5-mysql libapache2-mod-php5 mysql-server

See:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

