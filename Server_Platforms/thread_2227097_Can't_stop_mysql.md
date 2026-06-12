---
title: "Can't stop mysql"
date: 2014-05-30
forum: Server Platforms
---

### Post by gtozzi on 2014-05-30
Hi there,

I have two 14.04 LTS ubuntu stations (one is ubuntu server, while the other one is kubuntu). On both, I can't stop mysqld.

I can stop it by "/etc/init.d/mysql stop" or by "kill -9 <pid>". In any case, the process will respawn with a new PID.

Please help me get rid of it :D

Thank you!

---

### Post by steeldriver on 2014-05-30
Have you tried

```

sudo service mysql stop

```

---

### Post by gtozzi on 2014-05-30
> # service mysql stop
stop: Job sconosciuto: mysql
It means "unknown job"

---

### Post by gtozzi on 2014-05-30
So, I have now a more clear explanation of the problem:

**mysqld** is ran by **upstart** with the **respawn** option (*/etc/init/mysql.conf*): you can kill it, stab it, nuke it, it doesn't matter: upstart's **init** will always spawn a new process.

Only way to terminate it is by running: *service mysql stop*. If it doesn't work, you have to fix it.

When running **service**, it will look for an upstart job file, if it founds it, it will** ignore** the old init script (*/etc/init.d/mysql*) and call **initctl** that will communicate to **init** via **D-Bus** and ask it to stop the service.

In my case, communication is broken for some unknown reason but using **initctl** with the **--system** options works as workaround _by now_.

Any ideas on how to finally fix this so that **initctl **will run even without the **--system** option?

---

