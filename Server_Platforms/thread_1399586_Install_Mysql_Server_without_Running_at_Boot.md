---
title: "Install Mysql Server without Running at Boot"
date: 2010-02-05
forum: Server Platforms
---

### Post by user2037 on 2010-02-05
Is there a way to prevent the Mysql service from starting at boot? 

I recall there used to be a Services option in System Administration. But it is not there in Ubuntu 9.10.

---

### Post by Vegan on 2010-02-05
SQL servers are designed to be running at all times, they are not designed to run like an application.

If you are in need of a database, MySQL et al all are running in the background. They do not use a lot of RAM, but disk space is a function of the database size.

---

### Post by user2037 on 2010-02-06
> **Vegan said:**
> SQL servers are designed to be running at all times, they are not designed to run like an application.

If you are in need of a database, MySQL et al all are running in the background. They do not use a lot of RAM, but disk space is a function of the database size.

RAM and CPU are limited on my device. And while I'd like to keep Mysql server handy I don't always want it running in the background. 

As someone who has developed a few systems I'm aware of how servers usually work. This is not a continuously serving device.

And even on a server one may want to disable some services at boot to keep them ready as warm standby's.

Now, does anyone know how to prevent Mysql server from running at boot?

---

### Post by Xanthomryr on 2010-02-06
With update-rc.d you can stop the mysql-server from starting when booting.

Just use```
# update-rc.d -f mysql remove
``` to kick mysql out of the default runlevels. But this works only until the next update.

Have a look into this how-to for more information:

[http://www.debuntu.org/how-to-manage-services-with-update-rc.d](http://www.debuntu.org/how-to-manage-services-with-update-rc.d)

---

