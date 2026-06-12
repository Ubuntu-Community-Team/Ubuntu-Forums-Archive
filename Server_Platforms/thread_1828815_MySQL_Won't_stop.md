---
title: "MySQL Won't stop"
date: 2011-08-19
forum: Server Platforms
---

### Post by person287 on 2011-08-19
I'm having a load of problems with MySQL at the moment. It won't accept connections so I thought I'd stop it and restart it via stop mysql, but I get,

```
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.44" (uid=1000 pid=5295 comm="stop mysql ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
```

So then I thought I'd start again and reinstall as I only have one database that's backed up, via sudo apt-get purge mysql , but I get

```
E: Unable to locate package mysql
```

Does anybody have any ideas? I'm a bit lost.

Thanks

---

### Post by gordintoronto on 2011-08-19
Perhaps this will work:
sudo /etc/init.d/mysqld stop
or maybe just: sudo mysqld stop

See: [http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-mysql-server/](http://theos.in/desktop-linux/tip-that-matters/how-do-i-restart-mysql-server/)

Google is your friend.

---

### Post by jramshu on 2011-08-19
```
sudo /etc/init.d/mysql stop
```

You can substitute stop with start or restart.

EDIT: Oops, sorry gordintoronto, I was watching the tube while replying.

If you really want to remove it, it would something like:
```
sudo apt-get remove mysql-server
```

---

### Post by Sanados on 2011-08-22
you might want to add another 

apt-get autoremove

as apt-get remove mysql-server removes the generic mysql package but will most likely keep the server itself installed.

the auto-remove will most likely remove something like "mysql-server-5.1"

---

### Post by kohlanta on 2013-03-25
I get this same error when I don't have root priviledges.  try:
sudo service mysql stop

---

### Post by QIII on 2013-03-25
Thank you for sharing.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread **closed.***

---

