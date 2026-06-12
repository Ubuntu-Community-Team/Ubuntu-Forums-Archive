---
title: "Starting postgres with different '-D' value"
date: 2008-09-02
forum: Server Platforms
---

### Post by balckNwhite on 2008-09-02
Hi there,

After installing postgres using apt-get, when I run:

[FONT="Courier New"] sudo /etc/init.d/postgresql-8.3 start[/FONT]

The service starts with this process:

[FONT="Courier New"]/usr/lib/postgresql/8.3/bin/postgres -D /var/lib/postgresql/8.3/main -c config_file=/etc/postgresql/8.3/main/postgresql.conf[/FONT]

The issue is, the database was initialized using 'initdb' to a different directory. So it is not in '/var/lib/postgresql/8.3/main'. I would need to be able to startup the service with a different value for the '-D' parameter. Do you know how to do this?

I would be very grateful to any help.
Thank you in advance,

BNW

---

### Post by windependence on 2008-09-02
The -D paramter just tells Postgres where to find the database. Just change you value after the -D to reflect the location where you intitialized the database.

-Tim

---

