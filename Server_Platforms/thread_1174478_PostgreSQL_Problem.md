---
title: "PostgreSQL Problem"
date: 2009-05-31
forum: Server Platforms
---

### Post by Black Mage on 2009-05-31
I just recently installed postregel on my database server. I can access from that server but when I try to access from another server within the network I get this errpr:

psql: FATAL:  no pg_hba.conf entry for host "192.168.1.100", user "bon", database "bobsdb", SSL off

Does anyone have an idea what this error means?

---

### Post by windependence on 2009-05-31
Postgresql has networking off by default as do most Unix/Linux products for security. You need to go in the pg_hba.conf file and add an entry for your server IP. I seem to remember there is other places that you have to do this also.

This is the section you want to change:

```
# Allow any user from any host with IP address 192.168.93.x to connect
# to database "postgres" as the same user name that ident reports for
# the connection (typically the Unix user name).
#
# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD
host    postgres    all         192.168.93.0/24       ident
```
Substitute your IP subnet for the address in the code above as well as the name of your database for "postgres".


Postgresql is a very good enterprise class database, in the same class as Oracle. Congratulations on picking a good one.

-Tim

---

### Post by Black Mage on 2009-05-31
Thnx,
 I added this line to fix it:

host    all         all         [ip address]          [subnet mask]  md5

---

