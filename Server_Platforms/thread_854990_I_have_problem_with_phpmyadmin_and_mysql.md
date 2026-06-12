---
title: "I have problem with phpmyadmin and mysql"
date: 2008-07-10
forum: Server Platforms
---

### Post by joker40 on 2008-07-10
[B]I installed apache server and its works probably but i have problem with the mysql and the phpmyadmin i installed but nothing works 

and when i write mysql in the command this error will appear:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

i need help urgently so find some solutions for me because i tried this three days but i couldn't find any solution . [/B]

---

### Post by joker40 on 2008-07-10
i still waiting

---

### Post by carcdrcdr on 2008-07-10
> i still waiting

Chill out you only posted this 4 hours ago!

Lets start from the... TOP ;)
```
sudo /etc/init.d/mysql restart
```

Now confirm mysql is up with:
```
ps aux | grep mysql
```

You should now see mysql running.

Lets connect:
```
mysql -u username -p
```

IF you cannot connect STILL then post the output of:
```
ls -l /var/run/mysqld/mysqld.sock
```

and then:

```
ls -ld /var/run/mysqld/
```

---

