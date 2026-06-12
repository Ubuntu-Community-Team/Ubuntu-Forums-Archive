---
title: "I need help on how to automatically shutdown ubuntu 9.10 server."
date: 2010-10-13
forum: Server Platforms
---

### Post by maundinc on 2010-10-13
[SIZE=3]Hello,
[/SIZE][SIZE=3]
[/SIZE][SIZE=3]I have setup a server running on ubuntu 9.10 server for a company and don't want anybody to log into the server, so i need a way of shutting it down automatically let's say 5:00pm everyday.

best wishes[/SIZE]

---

### Post by slakkie on 2010-10-13
Shutting down a server? Weird request but eh.. not my box.

Have a look at cron:

man crontab
man cron

You would have something like this in the crontab of root:

```

0 18 * * * /sbin/shutdown -h now

```

Every day at 18:00 hrs it will issue a shutdown command.

---

### Post by SeijiSensei on 2010-10-13
Are you going to start it again manually every day?

When you say "login" what services are you specifically concerned about?  Samba? NFS? SSH?  You could write a cron script to shut down these services each day and start them again next morning.

Since it's a server how many people are allowed to log in normally anyway?  If they are using it for file sharing, make sure they have /bin/false as their default shell in /etc/passwd so they can't get a shell.  

If management is worried about people walking off with data after hours, rest assured they can walk off with it during working hours just as well.

---

