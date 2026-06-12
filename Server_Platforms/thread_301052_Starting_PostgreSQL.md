---
title: "Starting PostgreSQL"
date: 2006-11-16
forum: Server Platforms
---

### Post by JackRazz on 2006-11-16
When I installed PostgreSQL-8.1 in Ubuntu (Desktop Edition) and rebooted, I got a *[Failed to initialized HAL!]("http://www.ubuntuforums.org/showthread.php?p=1714229")* error.  I've figured out how to set the main cluster to start manually via the start.conf file to prevent PostgreSQL from starting up on boot up.  The HAL error is now gone.

I'm now trying to figure out how to start up PostgreSQL manually from a script or menu item.  I can start it up by opening up a shell window and doing the following.

```
sudo -s -u postgres
/usr/bin/pg_ctlcluster 8.1 main start
```

But the stuff below won't work in a script.

```
#!/bin/sh
sudo -s -u postgres /usr/bin/pg_ctlcluster 8.1 main start
```

I get a bunch of lines like this:
/usr/bin/pg_ctlcluster: line 19: my: command not found

This doesn't work.
```
sudo -s -u postgres
/usr/bin/pg_ctlcluster 8.1 main start

```

This command doesn't work either.
```
sudo /etc/init.d/postgresql-8.1 start
```

I'm a Linux newbie and I've be working on this off and on for a week.  I'm thinking that it must be related to permissions and the postgres user.  Can someone tell what I'm doing wrong or what kind of things I should be looking at to solve this problem.

Thanks - JackRazz

---

### Post by DRicher33 on 2006-11-16
Um, this may be a silly question but is the script chmod'd to executible and has the right perms?

---

### Post by JackRazz on 2006-11-16
Yes, but I don't use chmod.  Instead, I right-click on the script file, select properties, permissions and turn on *allow executing file as program*.

JackRazz

---

### Post by JackRazz on 2006-11-20
I resolved this problem.  pg_ctlcluster is used to start a cluster only and not the service.  I was turning off the cluster and then starting service, which resulted in not having my databases available.

So I turned off the postgresql Database Server from System/Administration/Services menu item and then simply started the service manually via *sudo /etc/init.d/postgresql-8.1 start*

---

