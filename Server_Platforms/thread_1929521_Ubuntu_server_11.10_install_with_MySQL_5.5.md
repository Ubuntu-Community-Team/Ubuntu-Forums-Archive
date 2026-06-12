---
title: "Ubuntu server 11.10 install with MySQL 5.5"
date: 2012-02-22
forum: Server Platforms
---

### Post by nervino on 2012-02-22
Hi All, I need to install Ubuntu server with the latest version of MySQL 5.5. Is it possible to choose this mySQL version during ubuntu installation?
If no, how can I upgrade  MySQL 5.1 to  MySQL 5.5 after ubuntu installation? Can somebody suggest me a guide?

Thank you

---

### Post by aura7 on 2012-02-22
Open the undergiven link
 
[http://www.mysql.com/downloads/mysql/#downloads](http://www.mysql.com/downloads/mysql/#downloads)
 
In this choose Debian Linux and download V5.5, after that uninstall the previous version and install this one using dpkg or simply doubling clicking it.

---

### Post by nervino on 2012-02-22
Thank you, I'll follow your suggestions.

---

### Post by zeljkojagust on 2012-02-22
You can also try Percona MySQL, it uses InnoDB engine instead of default MyISAM, and current version is 5.5. There is a .deb installation package, and also a nice guide how to set up an apt repository for installation. Also on [http://tools.percona.com](http://tools.percona.com) you have a great my.cnf generator, which makes it an all in one solution.

---

