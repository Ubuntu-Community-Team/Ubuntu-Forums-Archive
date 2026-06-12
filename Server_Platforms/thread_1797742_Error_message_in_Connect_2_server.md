---
title: "Error message in Connect 2 server"
date: 2011-07-05
forum: Server Platforms
---

### Post by amidboys on 2011-07-05
[LEFT]Hello. I have 2 servers, WebServer Application  and database server.[/LEFT]
  [LEFT]I define IP Valid  on WebServer, and when I connect  to this server from the internet, first page of my application is loaded But when the web server will be connected to the database server, I see error message.[/LEFT]
  [LEFT]But when I entered the application via a local network, I do not see any error message.[/LEFT]
  [LEFT]Additionally, the database server is not defined by any IP Valid.[/LEFT]
  [LEFT]Please Help Me[/LEFT]

---

### Post by rubylaser on 2011-07-05
You're are definitely going to need to provide more info if you want to get help.  I'm not even sure what type of database you're using (I assume MySQL).  If you are using MySQL, did you edit your /etc/mysql/my.cnf and comment out this line?
```
#bind-address           = 127.0.0.1
```Otherwise, you won't be able to make connections from a remote host.  Next, if you've done this, can you connect to the database from the remote computer via the mysql client from the command line?

> Additionally, the database server is not defined by any IP Valid.
I have no idea what this means.

---

