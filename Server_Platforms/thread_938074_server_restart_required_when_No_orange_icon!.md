---
title: "server restart required when?? No orange icon!"
date: 2008-10-04
forum: Server Platforms
---

### Post by bcn17 on 2008-10-04
I have got a server up and running that I'm controlling using ssh. One thing I was wondering about is basic package management and system updates. 

On my desktop machine a nice little icon pops up and notifies me that I need to update and upgrade. Furthermore, if (not that often but sometimes) a restart is required it lets me know. 

Am I expected to run aptitude update, safe-upgrade, etc just every once and a while to check? I suppose I could put a text file in the daily cron section.. but even if I had it auto update and upgrade what about restarts? How will I know if the packages upgraded will require a system restart?

---

### Post by cariboo on 2008-10-04
I personally use aptitude to check for updates once a week:

```
sudo aptitude update
```

and then to upgrade:

```
sudo aptitude safe-upgrade
```

I use safe upgrade as I would rather not be stuck with a server that doesn't work. :)

As far as restarting, the only time you need to restart is if there is a kernel update, and I don't bother if things are working as they should.

I wouldn't create a script for updating, as there is the chance that an unattended update could make your server unusable.

Jim

---

