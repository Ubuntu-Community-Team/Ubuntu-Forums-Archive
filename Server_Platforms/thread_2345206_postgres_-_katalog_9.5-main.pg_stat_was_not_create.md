---
title: "postgres - katalog 9.5-main.pg_stat was not created"
date: 2016-12-01
forum: Server Platforms
---

### Post by ykpafu3r on 2016-12-01
Hi, today i have a problem with postgres(i don't know why, yesterday all was ok).
Frist.
i don't connect to localhost:5432, when i check

```

sudo service postgresql status
&#9679; postgresql.service - LSB: PostgreSQL RDBMS server
   Loaded: loaded (/etc/init.d/postgresql; bad; vendor preset: enabled)
   Active: active (exited) since czw 2016-12-01 22:10:53 CET; 4min 40s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2732 ExecStop=/etc/init.d/postgresql stop (code=exited, status=0/SUCC
  Process: 2784 ExecStart=/etc/init.d/postgresql start (code=exited, status=0/SU


```

pass hours debugging...
and i saw that in path 
'/var/run/postgres/' or '/var/run/postgres' 
directory '9.5-main.pg_stat_tmp' doesnt exists. why?

when the directory created and postgres restarted.
i can connect to localhost on 5432 port. but status all the time

```

&#9679; postgresql.service - LSB: PostgreSQL RDBMS server
   Loaded: loaded (/etc/init.d/postgresql; bad; vendor preset: enabled)
   Active: active (exited) since czw 2016-12-01 22:22:00 CET; 4s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3890 ExecStop=/etc/init.d/postgresql stop (code=exited, status=1/FAILURE)


```


AND! when i reboot system again i do not connect to postgres ;/ why?

ubuntu 16.04

---

### Post by Graham_Willis on 2016-12-04
What's the state of PostgreSQL after reboot, is it actually running?
What is in PostgreSQL logs? I don't know where they're located, but it might be in **/var/log/postgresql**.

---

