---
title: "Can't remote connect to mysql on Edgy"
date: 2006-12-16
forum: Server Platforms
---

### Post by niklasro on 2006-12-16
Hi,

I've installed mysql on Edgy and granted remote access privileges like this
mysql>grant all on *.* to root@"myip" identified by "mypassword";

But when I try to connect from a remote computer access is denied.
I can ping the server from the mysql windows Admin GUI I am trying to connect from.
How do I resolve this so I can connect? Any help is greatly appreciated.

Thanks

Niklas

---

### Post by chrisfay on 2006-12-16
Try commenting out:

```
bind-address            = 127.0.0.1
```

...in your /etc/mysql/my.cnf and restarting

MySQL binds to 127.0.0.1 by default....

---

### Post by niklasro on 2006-12-17
:D :D :D 

Thanks!!! It works.

---

### Post by chrisfay on 2006-12-17
splendiferousnessness.....;)

---

