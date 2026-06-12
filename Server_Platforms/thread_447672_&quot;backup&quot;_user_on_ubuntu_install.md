---
title: "&quot;backup&quot; user on ubuntu install?"
date: 2007-05-18
forum: Server Platforms
---

### Post by tr333 on 2007-05-18
i tried creating a new user called "backup" only to find that it already exists with the default install.  What is this user used for?

---

### Post by craigp84 on 2007-05-18
Backing up stuff :-)

Actually, it's not used in ubuntu. But it can easily be.

I have in the past setup a sudo map like:

```
backup  ALL=NOPASSWD: /bin/tar cpvf /dev/st0 /etc /root ...
```

Once this is rolled out across your prod env, couple it with some ssh pubkey authentication goodness (remember you can limit what host(s) a key is valid from, and even what commands can be run- nice for the security paranoid :-) And then wire up a cron job as "backup" user to run the backups across a few hosts.

The benefits are mainly cleanliness - it keeps stuff organised instead of root's crontab becoming bloated.

-c

---

### Post by tr333 on 2007-05-18
looks a bit too confusing for my backup purposes...

might just stick with rsync for the moment.

---

