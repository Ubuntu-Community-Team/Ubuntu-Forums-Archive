---
title: "Multiple Servers installation on an Ubuntu Server"
date: 2017-11-29
forum: Server Platforms
---

### Post by linoxide on 2017-11-29
14:29 29.11.2017

Hello Guys,

is it possible to install multiple MySQL Servers instances on an Ubuntu Server like that is possible on Windows Server?

The goal is to have 10 MySQL Server instances in one Ubuntu Server installed. Each MySQL Server with his own port number and IP Address.

Is that possible? If yes..which extra tool should i use, for example Percona Server or MySQL cluster?

PS: I use an Ubuntu Server "without User Interface".

What´s the best solution for this scenario please? Thank you so much in advance.

---

### Post by Tadaen_Sylvermane on 2017-11-30
Id do it with lxd containers. Is there a reason you cant just have a single mysql server for everything?

---

### Post by SeijiSensei on 2017-11-30
It's a lot easier to have one MySQL server and multiple databases.  I support about half-a-dozen WordPress sites from a single server instance.

Perhaps if you explain the rationale for multiple servers, we can provide better advice.

---

### Post by cariboo on 2017-12-01
Moved to Server Platforms.

---

