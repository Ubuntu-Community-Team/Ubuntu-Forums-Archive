---
title: "need help, mysql cant start"
date: 2005-11-23
forum: Server Platforms
---

### Post by sickdude on 2005-11-23
ooh sh*t dudes

i cant start mysql, im trying /etc/init.d/mysql start

root@teletran:/home/sickdude# /etc/init.d/mysql start
root@teletran:/home/sickdude#


but nothing happens. i was removing postfix and this stopped mysql. i reinstalled postfix, and it never started mysql.

this server is for public use and the forum is offline because i was playing around so if someone can help me that would me great :)

thnx in advance

---

### Post by sickdude on 2005-11-23
apt-get install mysql-server

this did the trick very strange, very very strange, maybe a bug??

---

### Post by henriquemaia on 2005-11-23
[QUOTE=sickdude]apt-get install mysql-server

this did the trick very strange, very very strange, maybe a bug??[/QUOTE]

Maybe when you removed postfix, apt removed mysql-server as well. This is just a maybe, because I do not its dependencies.

---

