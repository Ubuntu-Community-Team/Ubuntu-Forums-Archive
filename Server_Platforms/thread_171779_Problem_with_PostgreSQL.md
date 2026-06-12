---
title: "Problem with PostgreSQL"
date: 2006-05-07
forum: Server Platforms
---

### Post by rensu on 2006-05-07
Have anyone had the same problem? If yes could someone help me please:(

Getting this error after installing postgresql-8.1:
 * Starting PostgreSQL 8.1 database server: main
The PostgreSQL server failed to start. Please check the log output:
LOG:  could not bind IPv4 socket: Cannot assign requested address
HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets
   ...fail!

And no there is not other postmater running on port 5432.

---

### Post by agile on 2006-05-10
Ditto. I'm on the hunt for the solution now. ] (*,)

---

### Post by LordHunter317 on 2006-05-10
Is  there something else using htat port?  What does 'netstat -pln --inet --inet6' say?

---

### Post by agile on 2006-05-10
AHA!

my loopback was missing! :)

double check that your /etc/network/interfaces has a loopback device configured.
mine had been moved to /etc/network/interfaces.back for some reason or another. :( mysterious.
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

---

### Post by rensu on 2006-05-10
In /etc/network/interfaces : 
getting those lines:
# The loopback network interface
auto lo
iface lo inet loopback

So I guess I have the lines what you were talking about. But it's still not working for me :(

---

