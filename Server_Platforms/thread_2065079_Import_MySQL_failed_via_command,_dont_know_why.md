---
title: "Import MySQL failed via command, dont know why"
date: 2012-10-01
forum: Server Platforms
---

### Post by Nixforce on 2012-10-01
Hi,

I have the SQL file on my server. Its not huge, only 250mb. 

I get this error when importing via the terminal.

ERROR 2006 (HY000) at line 1: MySQL server has gone away.

The sql file is local on the server, and im using this command.

mysql --user=USERNAME --pass=PASSWORD --host=SERVERHOST DATABASE < /PATH/FILE.SQL

It does ask me for username and password, and im sure those are correct.

Any help would be great!! Thanks

---

### Post by sandyd on 2012-10-01
> **Nixforce said:**
> Hi,

I have the SQL file on my server. Its not huge, only 250mb. 

I get this error when importing via the terminal.

ERROR 2006 (HY000) at line 1: MySQL server has gone away.

The sql file is local on the server, and im using this command.

mysql --user=USERNAME --pass=PASSWORD --host=SERVERHOST DATABASE < /PATH/FILE.SQL

It does ask me for username and password, and im sure those are correct.

Any help would be great!! Thanks

try
[http://bugs.mysql.com/bug.php?id=15220](http://bugs.mysql.com/bug.php?id=15220)

---

