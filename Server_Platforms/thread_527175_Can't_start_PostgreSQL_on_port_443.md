---
title: "Can't start PostgreSQL on port 443"
date: 2007-08-16
forum: Server Platforms
---

### Post by happyraul on 2007-08-16
I am trying to start PostgreSQL on port 443, but it does not work.  I have tried other ports, such as the default (5432 I believe) and 8080 and it works, but I want it on port 443.  I thought apache may be the reason it didn't work, but even with apache stopped, I still could not start it.  Other ports, like 25, also do not work.  Here is the output:

```

sudo /etc/init.d/postgresql-8.2 start
 * Starting PostgreSQL 8.2 database server                                                                                                                   
* The PostgreSQL server failed to start. Please check the log output:
2007-08-15 15:37:12 CDT LOG:  could not bind IPv6 socket: Permission denied
2007-08-15 15:37:12 CDT HINT:  Is another postmaster already running on port 443? If not, wait a few seconds and retry.
2007-08-15 15:37:12 CDT LOG:  could not bind IPv4 socket: Permission denied
2007-08-15 15:37:12 CDT HINT:  Is another postmaster already running on port 443? If not, wait a few seconds and retry.
2007-08-15 15:37:12 CDT WARNING:  could not create listen socket for "*"
2007-08-15 15:37:12 CDT FATAL:  could not create any TCP/IP sockets
[fail]

```

---

### Post by unixhead on 2007-08-17
It seems that PostgreSQL itself is bound to several default ports. Check pg_hba.conf in you Postgres conf directory.

---

### Post by colo on 2007-08-17
Two possible reasons come to mind:

1.) Postfix binds ports as an unrpivileged, non-root user, thus disallowing the use of well-known ports (all below 1025).

2.) A service is already running on port 443 - maybe some webserver that also listens for HTTPS-requests. You may not bind any given port more than one single time per interface listened on.

---

### Post by ihristov on 2007-08-17
> **colo said:**
> Two possible reasons come to mind:

1.) Postfix binds ports as an unrpivileged, non-root user, thus disallowing the use of well-known ports (all below 1025).

2.) A service is already running on port 443 - maybe some webserver that also listens for HTTPS-requests. You may not bind any given port more than one single time per interface listened on.

In your case it appears it's reason 1)

You could workaround this issue, by setting up a forwarding rule with iptables

---

### Post by happyraul on 2007-08-17
Yep, I used my router to forward 443 to the default postgres port.  It accomplished my goal, thanks everyone!

---

