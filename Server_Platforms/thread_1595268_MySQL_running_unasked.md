---
title: "MySQL running unasked"
date: 2010-10-13
forum: Server Platforms
---

### Post by Neo23x0 on 2010-10-13
I installed MySQL on my Ubuntu 10.04 desktop. 

As I need it only once a month I removed it from all runlevels but mysql is still running after boot up. "lsof" shows that it is running and listening for connections.

```
neo@ubuntu:~$ sudo lsof -i
[sudo] password for neo: 
COMMAND    PID  USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
sshd       927  root    3u  IPv4   7819      0t0  TCP *:ssh (LISTEN)
sshd       927  root    4u  IPv6   7821      0t0  TCP *:ssh (LISTEN)
avahi-dae  945 avahi   12u  IPv4   8107      0t0  UDP *:mdns 
avahi-dae  945 avahi   13u  IPv6   8108      0t0  UDP *:mdns 
avahi-dae  945 avahi   14u  IPv4   8109      0t0  UDP *:58234 
avahi-dae  945 avahi   15u  IPv6   8110      0t0  UDP *:49348 
cupsd     1090  root    5u  IPv6  71988      0t0  TCP ubuntu:ipp (LISTEN)
cupsd     1090  root    6u  IPv4  71989      0t0  TCP localhost.localdomain:ipp (LISTEN)
mysqld    1172 mysql   10u  IPv4   8497      0t0  TCP localhost.localdomain:mysql (LISTEN)

```

How can I evaluate what started the MySQL daemon?
WHy is it running?

Thanks for your help.

---

### Post by emgee3 on 2010-10-13
You sure you removed it from the runlevels correctly? 

```
sudo update-rc.d -f mysql disable
```

---

