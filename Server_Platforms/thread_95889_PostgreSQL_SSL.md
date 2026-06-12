---
title: "PostgreSQL SSL"
date: 2005-11-27
forum: Server Platforms
---

### Post by jsgaarde on 2005-11-27
After installing the PostgreSQL server I discovered that the daemon could not be startet:

 * Starting PostgreSQL 7.4 database server: main The PostgreSQL server failed to start. Please check the log output:
/usr/lib/postgresql/7.4/bin/postmaster: TCP/IP connections must be enabled for SSL [fail]

On postgres official site, it is written that in order to use postgreSQL with ssl enabled tcp/ip connections you must install openSSL. Since that is already installed on my system and postgresql will still not start, I decided to run without ssl.

ssl = false

in /etc/postgresql/7.4/main/postgresql.conf, but I'm not sure this is the way security experts would have done it. 

I can't find much about the issue in google, but I still think someone more knowlegable than me in this field should post an explaination on how to fix the issue correctly.

Best Regards

Jakob Simon-Gaarde

---

### Post by santo on 2005-11-29
while trying to get gForge installed, I notice the same problems:
> 
TCP/IP connections must be enabled for SSL


any suggestions on this one ?

Note: I don't want to disable ssl

---

### Post by mindwarp on 2005-12-04
Edit postgresql.conf and uncomment the line #tcpip_socket = true:

```

# - Connection Settings -

tcpip_socket = true

```

---

