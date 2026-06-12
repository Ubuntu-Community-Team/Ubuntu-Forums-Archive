---
title: "MYSQL Backups"
date: 2007-08-10
forum: Server Platforms
---

### Post by coxy on 2007-08-10
Can someone tell me what I need to backup when taking .sql backups. I know I don't need the information_schema but do I need to include the mysql database as well as any others I am backing up?

In my case I have databases called wiki, mysql and information_schema

Should I just back up wiki or do I also need the mysql database as well?

Thanks in advance.

---

### Post by kidders on 2007-08-11
Hi there,

There are a few quite different approaches to backing up SQL databases. One I use quite a bit is to simply dump databases to a file & gzip the result, but there are other options, depending on what sorts of databases you have, and whether you can afford to shut down the server for a few moments.

If an SQL dump preserves enough information for you to reconstruct your databases, the I would recommend doing that. It's certainly the most straightforward option.

---

### Post by elst on 2007-08-11
The "mysql" database holds settings that MySQL uses itself, such as usernames and passwords, so you definitely should back it up. IIRC, "information_schema" does not contain any information (just views), but should be relatively small, so you might as well.

---

