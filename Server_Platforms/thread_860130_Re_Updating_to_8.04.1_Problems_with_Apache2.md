---
title: "Re: Updating to 8.04.1 Problems with Apache2"
date: 2008-07-15
forum: Server Platforms
---

### Post by drbuggs on 2008-07-15
Hey

After upgrading from 7.10 to 8.04.1 Everything works except my Apache2 server with Php and Mysql.

Any Ideas whats been changed, the server is running, apache2 -k restart -v returns ok status. Mysql server seems to be running, i can log manualy onto Client of Mysql.

Suggestions apreciated.

buggs

---

### Post by Sef on 2008-07-15
Moved to server Platforms.

---

### Post by drbuggs on 2008-07-15
Ok seems i have to reconfig the server.

Hope i can salvage my mysql database ;(

---

### Post by drbuggs on 2008-07-15
Found the problem, kolab Wrecked on upgrading from 7.1 to 8.04.1, Uninstalled *Kolab* and restarted Apache and all works ( Except Kolab).

---

