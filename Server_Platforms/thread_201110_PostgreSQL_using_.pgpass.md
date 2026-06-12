---
title: "PostgreSQL using .pgpass"
date: 2006-06-21
forum: Server Platforms
---

### Post by odyn_owl on 2006-06-21
I want to make scripts that backup database, but pg_dump when execute asking for password.
I' wrotten [here]("http://www.postgresql.org/docs/8.1/interactive/libpq-pgpass.html") about password file, but this file didn't help me - script interept with error authentication failed for user "postgres".
May be somebody do that and can describe step by step what have to do.
thanks.

Server 6.06

---

### Post by wasare on 2006-09-03
export the environment variables PGUSER and PGPASSWORD

---

### Post by tarvid on 2007-05-08
Not wonderful but set 

host    all         all         127.0.0.1/32          trust

as the first line and restart postgresql.

Might want to put it back afterwards.

---

