---
title: "postgresql not starting"
date: 2010-02-01
forum: Server Platforms
---

### Post by map7 on 2010-02-01
I'm trying to install postgresql 8.3 on Ubuntu 8.04 LTS server and I'm running into problems starting it.

Commands I've done
# apt-get install postgresql postgresql-common

Things I've tried
Starting it manually

# /etc/init.d/postgrsql-8.3 start

Nothing appears in my /var/run/postgresql

When I try and start psql as the postgres user I get the following error

psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

I've been following the docs at: [https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

---

### Post by jjonesjr on 2010-03-02
Bump, I'm having the same problem.

Fresh install of 9.10, fresh install of postgresql via apt-get install postgresql, root (not just sudo, but real old fashioned root) gets no response via either:

/etc/init.d/postgresql-8.4 start or
/etc/init.d/postgresql-8.3 status

dmesg and var/log/syslog both give no clue as to postgres's problem, and var/log/postgresql is empty

---

### Post by jjonesjr on 2010-03-02
Looks like i fixed it via help in this thread:
[http://ubuntuforums.org/showthread.php?p=8389411&posted=1#post8389411](http://ubuntuforums.org/showthread.php?p=8389411&posted=1#post8389411)

The solution was to fully remove postgres and then reinstall it.  Don't ask me how or why the earlier install got corrupted:

#Remove postgres 
```
apt-get remove --purge postgresql-8.4*
```

#Remove all other dependent libraries
```
aptitude remove
```

#Re-install postgres
```
apt-get install postgresql-8.4
```

---

