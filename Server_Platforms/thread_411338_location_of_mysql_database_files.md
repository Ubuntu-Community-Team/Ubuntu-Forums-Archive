---
title: "location of mysql database files"
date: 2007-04-16
forum: Server Platforms
---

### Post by nix4me on 2007-04-16
Where are the mysql database files located?  I would like to find my tables so I can have my backup program back them up for me.  I know i can export them from mysql, but i would prefer a simple file copy for backup purposes.

nix4me

---

### Post by nix4me on 2007-04-16
Ok, i figured it out.  Instead of copying the files in /var/lib/mysql, i found the command mysqldump.  When added to my backup script, this command dumps my database perfectly.  Hope this helps others.

man mysqldump will help with the options.

nix4me

---

### Post by tone77 on 2007-04-17
you can also checkout MySQL hotcopy at [http://dev.mysql.com/doc/refman/5.0/en/mysqlhotcopy.html](http://dev.mysql.com/doc/refman/5.0/en/mysqlhotcopy.html)

---

