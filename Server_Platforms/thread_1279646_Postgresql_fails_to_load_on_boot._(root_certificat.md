---
title: "Postgresql fails to load on boot. (root certificate error)"
date: 2009-10-01
forum: Server Platforms
---

### Post by 6tangos on 2009-10-01
Hi, when booting Postgresql fails to load.
In /var/log/postgresql/log I have the following messages:

2009-10-01 10:10:55 BST LOG:  could not load root certificate file "root.crt": no SSL error reported
2009-10-01 10:10:55 BST DETAIL:  Will not verify client certificates.
2009-10-01 10:10:55 BST FATAL:  could not open configuration file "/etc/postgresql/8.3/main/pg_hba.conf": Permission denied
2009-10-01 10:14:22 BST LOG:  could not load root certificate file "root.crt": no SSL error reported
2009-10-01 10:14:22 BST DETAIL:  Will not verify client certificates.
2009-10-01 10:14:22 BST FATAL:  could not open configuration file "/etc/postgresql/8.3/main/pg_hba.conf": Permission denied
2009-10-01 10:15:52 BST LOG:  could not load root certificate file "root.crt": no SSL error reported
2009-10-01 10:15:52 BST DETAIL:  Will not verify client certificates.
2009-10-01 10:15:52 BST FATAL:  could not open configuration file "/etc/postgresql/8.3/main/pg_hba.conf": Permission denied

Running Ubuntu 9.04 (Desktop Edition for the graphics) Kernel 2.6.28-15.
RM Machine Intel core Duo.

Any ideas?

Many thanks.

---

### Post by windependence on 2009-10-01
Did you install Postgresql from packages? It looks like you never configured it. This may help:

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

-Tim

---

### Post by 6tangos on 2009-10-01
Hi, I'm pretty sure that I compiled and installed this copy as I wanted the latest version of Postgres and PostGIS. Once the machine has booted if I do
'su Postgres' then 'pg_ctl start' the db starts fine (no errors in the log). I can access the db locally and connect from other machines that I've allowed in pg_hba.conf I can also successfully connect over the network using the udig GIS client.

The only possible complication is that the db is in a non standard location (thus when starting I do 'pg_ctl start -D /mypath/todb').

Thanks

Tom

---

