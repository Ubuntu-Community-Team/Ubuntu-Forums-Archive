---
title: "Connect a webserver with a database server with putty (No tunnel)"
date: 2015-08-26
forum: Server Platforms
---

### Post by leuzingercedric on 2015-08-26
Hey guys,
im new to linux and i need to get a simple connection between a webserver and a databaseserver.

- Both have different ip adresses
-i shouldnt use a tunnel, my mentor told me i should use a "simple" connection
- im not allowed to install mysql on the webserver, so i need a connection from the webserver to the database server to get the data from there
- i need to use putty for this project

shortly a word about me, i startet an education to a it professional a week ago and need to finish a LAMP project until friday and i have no clue.
Googling is limited because all ppl out there explain it only with an local Mysql server. 

Would be nice if someone can help me with a simple, for newbies explained solution.


Ty mates
cleuzing

---

### Post by SeijiSensei on 2015-08-26
You can specify the remote host and port in [mysqli_connect()]("http://php.net/manual/en/function.mysqli-connect.php").  The second entry in the contributed notes section of the linked page provides a simple example.

Are you responsible for the MySQL server as well?  If so, you'll need to enable remote access by editing my.cnf and disabling the bind-address directive like this:
```
#bind-address = 127.0.0.1
```
That tells MySQL to listen on all network interfaces rather than just "localhost."

---

