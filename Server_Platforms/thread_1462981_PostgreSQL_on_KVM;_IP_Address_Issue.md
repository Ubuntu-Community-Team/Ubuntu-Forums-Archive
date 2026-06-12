---
title: "PostgreSQL on KVM; IP Address Issue"
date: 2010-04-26
forum: Server Platforms
---

### Post by jasond496 on 2010-04-26
I'm currently in the process of setting up a virtualized production webserver environment, using Karmic server.  I'm having a bit of trouble with the virtual PostgreSQL server portion.

I have the host and database guest going over a bridged network connection to the regular LAN, using regular 192.168.0.X IP addresses, and can connect to PostgreSQL from a LAN machine just fine.  However, I also have a virtual network running on the host in the 192.168.122.X range so that the virtual database server can connect to the virtual web server.

This is where the problem comes in.  PostgreSQL binds and listens on 192.168.0.36 just fine, but will listen on 192.168.112.2, giving this in the log:
```
2010-04-26 15:23:51 UTC LOG:  could not bind IPv4 socket: Cannot assign requested address
2010-04-26 15:23:51 UTC HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
2010-04-26 15:23:51 UTC WARNING:  could not create listen socket for "192.168.112.2"
```

The virtual database server will respond to ping at 192.168.112.2, and will allow me to ssh in, from both the host and the other webserver guest.  Also `netstat -l' on the database server shows postgres and ssh listening on 192.168.0.36, but only ssh on 192.168.122.2.

Any ideas would be greatly appreciated.

---

### Post by jasond496 on 2010-04-26
I managed to solve this.  I just had to add a record in the hosts file to point to the secondary IP and hostname on the virtual webserver.  Then, rather than adding the secondary IP to listen_addresses in postgresql.conf, I used the secondary fully qualified host/domain name, and now it is actively listening.

---

