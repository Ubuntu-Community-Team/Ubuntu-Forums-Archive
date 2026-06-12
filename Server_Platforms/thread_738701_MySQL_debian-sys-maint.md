---
title: "MySQL debian-sys-maint ??"
date: 2008-03-28
forum: Server Platforms
---

### Post by jazee on 2008-03-28
What is the purpose of the debian-sys-maint MySQL user. He seems to keep kicking on and running table checks at the worst times of the day.

---

### Post by Oldsoldier2003 on 2008-03-31
> **jazee said:**
> What is the purpose of the debian-sys-maint MySQL user. He seems to keep kicking on and running table checks at the worst times of the day.

the debian system maint user is the system account to run Mysql. If you are having problems with table checks being run you should probably look at the options in mysqladmin or phpmysqladmin (which ever you happen to be using) or look in your crontabs ...

---

### Post by jazee on 2008-04-03
does it use environmental variables to define when it runs or what? Not sure where to check to tell it when to run the table checks.

---

### Post by Oldsoldier2003 on 2008-04-03
> **jazee said:**
> does it use environmental variables to define when it runs or what? Not sure where to check to tell it when to run the table checks.

its very likely that you have a cronjob set to run 
```

mysqlcheck -Aao –auto-repair -u root -p[password] > /dev/null 
```

---

### Post by jazee on 2008-04-03
Just checked all the crontab didn't see any script running that would do this. Any other ideas of places to check.

---

### Post by Oldsoldier2003 on 2008-04-04
> **jazee said:**
> Just checked all the crontab didn't see any script running that would do this. Any other ideas of places to check.

look in
```
 /etc/cron.d
/etc/cron.daily
/etc/cron.hourly
/etc/cron.weekly
/etc/cron.monthly
```

---

