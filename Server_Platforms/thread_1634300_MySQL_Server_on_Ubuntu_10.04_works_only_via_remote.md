---
title: "MySQL Server on Ubuntu 10.04 works only via remote access, not local"
date: 2010-11-30
forum: Server Platforms
---

### Post by TheFr00n on 2010-11-30
Hi All,

So I've got an Ubuntu desktop machine running 10.04. I've got MySQL Server installed on it, and I want to connect to it using OpenOffice Base as a frontend.

If I tunnel in via SSH from a remote computer, I can connect flawlessly to the database using OpenOffice, with the MySQL Connector.

But if I am sat at the local machine, it will not connect (also using the Connector). I get the following error:

```
Can't connect to local MySQL server through socket '/tmp/mysql.sock'
```

I know the server is running. I know I can connect to it remotely. Through the remote connection, I can do all kinds of amazing things to do the database.

So why won't it let me do anything from local?

I'm going maaaaaaaaaaaaaaaaaaad.

---

### Post by TheFr00n on 2010-11-30
OK, I eventually figured this one out myself through the mighty google.

For some reason, the MySQL Connector for OpenOffice is to blame. It does not understand what localhost is. However, it does know that 127.0.0.1 is.

Replacing localhost with 127.0.0.1 when using the connector fixed the problem. Magic.

---

