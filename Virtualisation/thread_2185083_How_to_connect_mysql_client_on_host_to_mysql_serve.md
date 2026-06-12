---
title: "How to connect mysql client on host to mysql server in lxc container?"
date: 2013-10-31
forum: Virtualisation
---

### Post by andygrove on 2013-10-31
Hi,

I have created a linux container using lxc and installed mysql server. Within this container I can telnet to 127.0.0.1 port 3306 as expected. The IP address of this container is 10.0.3.210.

From the host, if I try to telnet to 10.0.3.210 port 3306 I get connection refused. I have been reading various articles about setting up NAT but I don't know if that is really what I need in this situation.

I'd appreciate any pointers on how I can make this work.

Thanks,

Andy.

---

### Post by Habitual on 2013-11-01
bind-address=10.0.3.210 in /etc/my.cnf
restart mysql-server and try again.

---

### Post by andygrove on 2013-11-01
Thanks for the tip. Unfortunately that did not work.

---

### Post by Habitual on 2013-11-02
> **andygrove said:**
> Unfortunately that did not work.

Did you restart mysql-server after editing the my.cnf on the container and re-try ```
telnet 10.0.3.210 3306
``` ?

mysql >```
grant all on db_name.* to 'mysql_username'@'your_ip' identified by 'mysql_password'; flush privileges;
```

"mysql_username" can be "FredFlinstone" if you so choose, and 
"mysql_password" can be "TheGreatGazoo" for all that it matters.

```
telnet  10.0.3.210 3306
``` is the real test before privs are granted.

you can 'view' the mysql-server allowable connections after connecting to mysql using >
mysql > 
```
use mysql; select host, user from user;
```

---

### Post by andygrove on 2013-11-05
@Habitual,

Thanks for sticking with this... I do have it working now. I had made an error when editing the my.cnf the first time (I ended up with two bind-address instructions).

Thanks!

Andy.

---

### Post by Habitual on 2013-11-05
Glad it worked out!
(and you stuck with it also!!!)

Mad Props.

John

---

