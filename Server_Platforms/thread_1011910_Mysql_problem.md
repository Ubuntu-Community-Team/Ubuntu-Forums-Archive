---
title: "Mysql problem"
date: 2008-12-15
forum: Server Platforms
---

### Post by white_shadow on 2008-12-15
Hi

i have this problem with mysql.

When i was working on server machine it works ok

but i try this from other machine (internet or in my home network) i get this error:

ERROR 2003 (HY000): Can't connect to MySQL server on 'abserver.no-ip.org' (10061)

How could i solve this error?

Marco

---

### Post by Fire_Chief on 2008-12-15
You need to configure MySQL to listen on the network. The my.conf file I think is where you uncomment the line to listen on port 3306. Then restart MySQL and it should allow connections over the network.

---

### Post by cdenley on 2008-12-15
After configuring mysql to listen for remote connections, you would also need to grant user access from remote hosts.
```

grant all on mydatbase.* to 'user'@'192.168.0.xx' identified by 'mypassword';

```
You should avoid doing this, especially over the internet. This is disabled by default for a very good reason.

---

