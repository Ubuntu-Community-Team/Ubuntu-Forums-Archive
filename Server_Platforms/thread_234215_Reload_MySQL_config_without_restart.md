---
title: "Reload MySQL config without restart?"
date: 2006-08-11
forum: Server Platforms
---

### Post by djvishnu on 2006-08-11
Is it possible to reload the mysql configuration without restarting?

I have to add a bind "ip" to my.cnf on a radius accounting server, but I do not want to restart the whole service.

---

### Post by etechsupport.net on 2006-08-11
MySQL settings are loaded in RAM of your system. There's no other way to flush previous memory other than restarting MySQL.

---

### Post by Kurt` on 2006-08-11
etechsupport.net that's not quite true...

Try # sudo /etc/init.d/mysql reload

:)

---

