---
title: "Database server"
date: 2008-04-03
forum: Server Platforms
---

### Post by akks on 2008-04-03
Hi,
 This is what i am trying for:
 
 Install a database (Oracle, or MySQL) on one of the PC's running Linux (any version). Make this databse available over all the PC's over the LAN. I mean users shoud be able to login remotely into this database over a LAN. i have done this for single desktops. Just want to know if this s possible. I want to do this as a part of my project.

---

### Post by 505 on 2008-04-03
Yes, it is possible with MySQL. Just install the MySQL server from the repositories. In the default configuration only the local machine can access the database, but you can easily change this. Open the file /etc/mysql/my.cnf and find 'bind-address           = 127.0.0.1' You can comment out the line (with #) to enable listening from any PC, or you LAN IPs to only accept computers on you LAN.

---

### Post by gvoima on 2008-04-03
I also recommend using MySQL GUI Tools, they help alot if you haven't used mysql command line.
[http://dev.mysql.com/downloads/gui-tools/5.0.html]("http://dev.mysql.com/downloads/gui-tools/5.0.html")
You should also find them in the repositories.

---

### Post by hyper_ch on 2008-04-03
furthermore you have to unlimit the normal mysql users in the mysql-db to not only use "localhost"

---

### Post by akks on 2008-04-03
Thank you guys.. But just wanna know if this is possible in ORACLE.

---

### Post by ClarkEveretts on 2008-04-04
You can try Oracle 10g Express Edition.

---

