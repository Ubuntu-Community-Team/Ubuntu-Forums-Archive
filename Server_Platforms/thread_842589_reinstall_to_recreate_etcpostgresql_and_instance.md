---
title: "reinstall to recreate /etc/postgresql and instance?"
date: 2008-06-27
forum: Server Platforms
---

### Post by jeffk on 2008-06-27
What aptitude/apt-get commands do I invoke to do a complete reinstall of postgresql-8.3 and components, with a new /etc/postgresql tree being created.

My Ubuntu 8.04 Hardy postgresql-8.3 got messed up while trying to accomodate an application's authentication requirements. I wanted to start over, stopped the server, deleted /var/lib/postgresql and /etc/postgresql

Now running sudo aptitude reinstall postgresql does not seem to configure a new postgresql instance.

Thanks.

---

### Post by forger on 2008-06-27
try the following:
```
sudo aptitude purge postgresql-8.3 postgresql-common
```
if it's messed up and can't remove postgresql:
```
sudo dpkg -P postgresql-8.3
```

then continue
```
sudo rm -rf /etc/postgresql/
sudo rm -rf /etc/postgresql-common/
```
and install postgresql again:
```
sudo aptitude install postgresql-8.3 postgresql-common
```

P.S. I think the default conf file is: /usr/share/postgresql/8.3/postgresql.conf.sample

---

### Post by Linux Lurker on 2008-10-29
[QUOTE=forger;5274336]try the following:
```
sudo aptitude purge postgresql-8.3 postgresql-common
```
if it's messed up and can't remove postgresql:
```
sudo dpkg -P postgresql-8.3
```


--------------
EXCELLENT
I've been trying to get a clean install of postgres and couldn't get by uninstalling it first because config and server.key were missing.

Now I've cleanly installed and will proceed with the next challenge of making it work.

I wanted to provide a "Thanks" for the above, but the link is missing from this thread. Because it's older?

Anyway.  THANKS!

---

### Post by kirenpillay on 2008-11-17
Hi,

Thanks you, I've had the same problematic experience.

Regards
Kiren

---

