---
title: "Cron Job Email on Error script help"
date: 2009-01-27
forum: Server Platforms
---

### Post by tmcmulli on 2009-01-27
I have several cron jobs running that work well, and I get notified by a .forward to my gmail acct.  Does anyone have a script that would only notify me in case of an error??  The cron jobs are simple backup jobs using rsync:

```
0 1 * * * rsync -avz --exclude="samba/iTunes Music/**" -e ssh /home/samba/samba username@backup.backupserver.com:daily
```

The 12 or so emails are great, but I really just want to know when something is wrong, like my fail2ban emails...

Any help GREATLY appreciated!

---

### Post by mlalkaka on 2009-03-10
I haven't tried any of these yet, here you go:
Cronic ([http://habilis.net/cronic/](http://habilis.net/cronic/))
Shush ([http://web.taranis.org/shush/](http://web.taranis.org/shush/))
Cronwrap ([http://www.uow.edu.au/~sah/cronwrap.html](http://www.uow.edu.au/~sah/cronwrap.html))

---

