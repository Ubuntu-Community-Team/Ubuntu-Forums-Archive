---
title: "Is the server running locally and accepting connections on Unix d socket postgresql"
date: 2014-12-22
forum: Server Platforms
---

### Post by cesar15 on 2014-12-22
Hi, I´ve read many similar forum discussions about this but I have not been able to solve the problem. I installed postgresql 9.1 on ubuntu 12.04 (not really a server machine, but virtualized in VirtualBox). Yesterday I was able to restart (and start) postgresql server but not today after many trials.

In postgresql.conf i have listen_addresses='*' and port=5432 and unix_socket_directory = 'var/run/postgresql'

I´ve looked into that directory but it seems to be empty.

I´ve tried: locate PGSQL.5432 but there´s no results

My server ip is set like 192.168.1.211 and ping -c 4 192.168.1.211 seems to be ok.

Tried many solutions (like chmod 777 /var/run/postgresql) and nothing seems to fix it.

It´s maybe and stupid issue and I´m not being able to solve it as i don´t have a high level of knowledge on those systems.

Full error messages: after sudo service postgresql restart -- > The postgresql server failed to start. Please check the log output. After sudo psql -- > could not connect to server: the file or directory does´nt exist. Is the server running locally and accepting connections on Unix domain socket "var/run/postgresql/.s.PGSQL.5432?

Postgresql version: 9.1

Just after starting ubuntu, this is the log that i get with tail /var/log/postgresql/postgresql-9.1-main.log:

CET LOG: could not open temporary statistics file "pg_stat_tmp/pgstat.tmp": permission denied.

CET LOG: received smart shutdown request

CET LOG: autovacuum launcher shutting down.

CET LOG: shutting down

CET PANIC: could not open control file "global/pg_control": permission denied

CET LOG: background writer process (PID 7151) was terminated by signal 6: Aborted

CET LOG: terminating any other active server processes

CET LOG: could not open temporary statistics file "pg_stat_tmp/pgstat.tmp": permission denied.

CET LOG: abnormal database systema shutdown.

Any idea about what to try?

---

### Post by nerdtron on 2014-12-22
Isn't posrtgresql library in the /var/lib/posrtgresql folder? the permission on this folder should be owned by postgresql user.

---

### Post by cesar15 on 2014-12-22
With so few words you have made a big favour to me. 

I´ve just made: 

```
sudo chown -R postgres:postgres /var/lib/postgresql 
```

And now postgresql is starting fine. So wrong permissions, maybe modified by myself, I´m not sure.

Thanks so much for your help. Kind regards.

---

### Post by cesar15 on 2014-12-22
I´d like to mark the thread like solved but I don´t know how to do it...

---

### Post by QIII on 2014-12-22
In the menu bar just above your first post, select "Thread tools" and then "Mark this thread as solved."

---

### Post by nerdtron on 2014-12-22
Glad to hear you sorted it out. :D

---

