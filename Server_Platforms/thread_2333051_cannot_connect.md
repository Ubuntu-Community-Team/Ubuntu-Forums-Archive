---
title: "cannot connect"
date: 2016-08-06
forum: Server Platforms
---

### Post by Vegan on 2016-08-06
still cannot connect with workpress to mysql

wonder what else is wrong?

use, database but workpress cannot connect

i disabled the local host so it should be connectable

---

### Post by QIII on 2016-08-06
Is this related to another of your posts?

---

### Post by Vegan on 2016-08-06
i got those working more or less, 

my server is located at 



but cannot seem to get MySQL to connect

i edited the config file 0.0.0.0 and #the skip-external-locking

---

### Post by Vegan on 2016-08-06
testing from the console, i can log in local host to the account with mysql 

i tried the firewall tool, seems to be a timeout

sudo ufw allow 3306/tcp

so not real sure what gives

---

### Post by cariboo on 2016-08-06
Is mysql located on the same server, or somewhere else?

---

### Post by Vegan on 2016-08-06
finger is not working and ping is not working

---

### Post by Vegan on 2016-08-06
mysql is on it own server elsewhere it the cloud

---

### Post by cariboo on 2016-08-06
Hopefully you haven't opened up mysql access to the world, as it will probably cause you a whole lot of problems.

---

### Post by Vegan on 2016-08-06
they will have to use 256-bit passwords to get past the login

the problem is with MySQL, I can telnet into the VM no problem

---

### Post by cariboo on 2016-08-06
In /etc/mysql/mysql.conf.d/mysqld.cnf do you have:

```
bind-address            = 127.0.0.1
```

commented out, so that mysql listens on any interface?

Just a warining, this could lead to your server being compromised if done improperly.

---

### Post by Vegan on 2016-08-07
the problem was the azure firewall, opened the port and bang i am in

I have strong passwords on the sites but I would like to modify them so they are limited to *.azurewebsites.net instead of %

root is console only and that is very strong password too

---

