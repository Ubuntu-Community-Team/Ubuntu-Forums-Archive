---
title: "mysql"
date: 2010-06-14
forum: Server Platforms
---

### Post by shanetlbrt on 2010-06-14
I have the command line version of mysql installed on the server. How do I install/access it through my browser? (I can already access the /var/www through my browser)

---

### Post by dapperdanny77 on 2010-06-14
/var/www is the document root of the default apache install - this has nothing to do with mysql.

you cannot access mysql from your browser without installing some pieces of software like phpMyAdmin (which is a mysql admin tool)

apache is a webserver, serving http protocol
mysql is a database server 
both usually working together as foundation for web applications written in php,perl,java or whatever

---

### Post by shanetlbrt on 2010-06-16
I know that, I was just wondering how to install phpmyadmin. But I downloaded it and FTP'd to my server..

---

### Post by terazen on 2010-06-17
You downloaded a tar.gz file?  I haven't used it in years, but I'm pretty sure there is a README file in there once you extract it.

---

