---
title: "[SOLVED] problem for remote access to postgres"
date: 2008-11-11
forum: Server Platforms
---

### Post by vitotol on 2008-11-11
hello guys i try to connect to a postgress server through pyPgSQL
but i get this respone:

libpq.DatabaseError: could not connect to server: Connection refused
Is the server running on host "10.0.0.3" and accepting
TCP/IP connections on port 5432?

i edited the postgres.conf and tcp_listen now is true.
i also add a line into pg_hba. what else should i try???:confused:

---

### Post by vitotol on 2008-11-12
ok i solved it.

---

