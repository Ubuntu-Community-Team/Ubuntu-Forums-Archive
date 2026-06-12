---
title: "Back up"
date: 2009-06-04
forum: Server Platforms
---

### Post by warvita on 2009-06-04
I'm new to Linux running on Ubuntu Desktop and Server 8.04LTS I need to a string which could be backing up my server every day at a specific time please help i'm in a dilemma and on a ticking time bomb in case of problem:(

---

### Post by smileypaul on 2009-06-04
Backing up data?

Use cron and rsync, or even cp -Ruv.

examples:

rsync -avzru /dir/to/be/backed/up /destination

or

cp -Ruv /dir/to/be/backed/up /destination

You can run either of those as a cron job in /etc/crontab

---

### Post by ZeldeR on 2009-06-04
rsync is better ;)

```
crontab -e
```

paste it in it and specify a time

15=m
3=h

```
15 3 * * * rsync -azv /* root@otherserver:/opt/
```

this is the very simple way to backup data :)

---

