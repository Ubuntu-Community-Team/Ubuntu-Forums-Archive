---
title: "[SOLVED] Postgres from remote ip"
date: 2008-09-25
forum: Server Platforms
---

### Post by rax_m on 2008-09-25
Hi 

I'm trying to get postgres to accept connection/authenticate when I login via my remote IP and not localhost. 

I have edited postgres.conf and set listen_addresses='*'

I have edited pg_hba.conf and added the following :
host    all         all         192.168.0.0 255.255.255.0           password

I have tried md5 as well for authentication type. 

My PHP application in which the user has to login with database userid and password gives the following error: 

Warning: pg_connect() [function.pg-connect]: Unable to connect to PostgreSQL server: FATAL: no pg_hba.conf entry for host "192.168.1.217", user "user", database "Test", SSL off in /var/www/ORI_Instruments/connect.php on line 4

Anyone have ideas on how to fix this please?

Thanks
Rax

---

### Post by lykwydchykyn on 2008-09-25
your entry in pg_hba.conf opens the server to connections from hosts on 192.168.0.0.  From your error message, your server seems to be on 192.168.1.0.  So you need to change your pg_hba.conf to allow hosts on that network, then restart postgres.

Use md5, not password, btw.

---

### Post by rax_m on 2008-09-26
Thanks.. I eventually figured that out and was just posting to say the same :)

---

