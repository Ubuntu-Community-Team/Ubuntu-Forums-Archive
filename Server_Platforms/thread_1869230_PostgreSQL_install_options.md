---
title: "PostgreSQL install options"
date: 2011-10-25
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-10-25
Would like to learn PostgreSQL 9.0 and want to install it onto a Ubuntu 11.04 Server.

Aware of 11.10 version but have had all sorts of issues with Unity.

Better to install when installing the server and upgrade, or clean install when server up and running?

TIA

---

### Post by vasile002 on 2011-10-25
It doesn't really matter when you install it as long as there are no older files(you can use purge to remove everything).

---

### Post by ChrisRChamberlain on 2011-10-26
Thanks vasile002

Decided to install in 11.10, but use Ubuntu Classic desktop.

---

### Post by darkod on 2011-10-26
> **ChrisRChamberlain said:**
> Would like to learn PostgreSQL 9.0 and want to install it onto a Ubuntu 11.04 Server.

Aware of 11.10 version but have had all sorts of issues with Unity.

Better to install when installing the server and upgrade, or clean install when server up and running?

TIA

You are aware that Desktop and Server are two separate versions, right? The server version by default comes with command line (it does not install any graphical environment, no Unity, no Gnome 2/3).

You can add graphic environment, but it is not really recommended on a server because in general it creates security risks. On a simple "to learn" server it wouldn't matter, but if you are serious about learning I guess you better do it in text mode and start learning the text mode (commands) too, if you are not familiar with it.

EDIT PS. Also for server usually only LTS releases are recommended. Again, as test server it doesn't really matter, but... Right now the latest LTS is 10.04 LTS and the next will be 12.04 LTS, in six months.

PPS. With all of the above said just to clarify that the Desktop version can also be used as a server of course. After installation (it doesn't ask you during) you can add PostgreSQL, MySQL, Apache, Samba file server, what ever you want.

---

### Post by ChrisRChamberlain on 2011-10-27
darkod

Thanks for your reply, the content of which has been noted.

---

