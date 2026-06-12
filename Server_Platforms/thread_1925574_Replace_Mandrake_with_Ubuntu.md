---
title: "Replace Mandrake with Ubuntu"
date: 2012-02-14
forum: Server Platforms
---

### Post by philipballew on 2012-02-14
I have an old (2.6.11) mandrake box that i want to whipe and run ubuntu on. how can i find out whats going on with this server and have the server run ubuntu yet still have the seme functions and perform the same tasks. I need to know where to find the stuff the system is doing would be, like scripts and what apps are installed. is that easy to do? the server currently talents into a other server and reads a database. yeah, it had talent when i found it, I plan to install ssh.

---

### Post by aeiah on 2012-02-15
automated processes will be triggered by cron, so you should probably start by looking at any cron tables that are on the system. if there are several users, you should check each one's cron table. to list the current user's cron, just issue the command:
```
crontab -l
```

for root's crontab, you should be able to do:```
sudo crontab -l
```

you also might want to see what's currently running. there may be a nicer way, but im not familiar with mandrake. this will list all the current processes:
```

ps aux
```
or sometimes
```

ps -aux
```

the easiest way to copy the crontabs to a file is to pipe it somewhere. if you use two pointy brackets instead of one, it'll append to the file, so you can use the same command with each crontab if there's more than one and have it save them to the same place

```

crontab -l >> /path/to/crontab.backup

```

you should also probably look at anacron, which is similar, and make sure you have access to any servers that the mandrake server accesses so you can generate new ssh-keys when you reinstall.

using clonezilla or just installing ubuntu on a different hard drive would probably be helpful if you're concerned that you'll remove something you later might need. you could then restore mandrake if need be.

---

