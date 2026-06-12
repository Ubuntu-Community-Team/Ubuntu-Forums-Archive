---
title: "cpu issues with mysql database"
date: 2013-12-13
forum: Server Platforms
---

### Post by pascalfares on 2013-12-13
Mysql is causing a very hight cpu usage and cause some freeze on the server. 

DO you have some advises?

Regards

---

### Post by nerdtron on 2013-12-13
What is the specs of your server? How many sql queries/transactions do you expect per second?
You might want to edit your my.cnf file like the following:

```
[COLOR=#333333]max_connections         =       800
[/COLOR]skip-host-cache
skip-name-resolve
max_allowed_packet             = 16M
max_connect_errors             = 1000000

```

---

### Post by tgalati4 on 2013-12-14
Install *htop* and watch the load for a while.  What does the memory look like?

```
sudo apt-get install htop
htop
free
```

If you are out of RAM and using swap then that will slow things down.

---

