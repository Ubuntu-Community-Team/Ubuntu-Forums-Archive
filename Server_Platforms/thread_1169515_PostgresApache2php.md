---
title: "Postgres/Apache2/php"
date: 2009-05-25
forum: Server Platforms
---

### Post by JonoT on 2009-05-25
I installed Postgres on my laptop, which works fine. 

I install Apache2 which also works fine. I tried doing a simple index.html which says:

[html]<html><body><h1>It works!</h1></body></html>[/html]which works.

I also write a simple php script with some select statements from the database and that gives me output too. 

But when I try to run my database on apache, I get an error. Can anyone give me any ideas about anything that I may have missed?

[php]
Warning:  pg_connect() [function.pg-connect]: Unable to connect to PostgreSQL server: could not connect to server: No such file or directory     Is the server running locally and accepting     connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"? in /var/www/mymyunsw/lib/db.php on line 11
Can't connect to database in '/var/www/mymyunsw/lib/db.php', line 12, _dbError() in '/var/www/mymyunsw/index.php', line 6, dbConnect()  [/php]
Thanks,
Jonathan.

---

### Post by LepeKaname on 2009-05-26
From my point of view, it may be related to your security configuration in postgres? I'm not sure...

check your /etc/postgres/(version)/main/pg_hba.conf

Something like this: (check manual)

# Database administrative login by UNIX sockets
local   all         postgres                          ident sameuser

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD

# "local" is for Unix domain socket connections only
local   all         all                               md5
# IPv4 local connections:
host    all         all         192.168.0.0/24       trust
# IPv4 local connections:
host    all         all         127.0.0.1/32          md5
# IPv6 local connections:
host    all         all         ::1/128               md5

---

