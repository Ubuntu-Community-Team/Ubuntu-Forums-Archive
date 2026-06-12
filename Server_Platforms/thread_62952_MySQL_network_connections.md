---
title: "MySQL network connections"
date: 2005-09-06
forum: Server Platforms
---

### Post by eantoranz on 2005-09-06
How can I make MySQL listen to remote connections?

```

# mysql -h 127.0.0.1 -u mambo
ERROR 2003: Can't connect to MySQL server on '127.0.0.1' (111)

```

---

### Post by LordHunter317 on 2005-09-06
It should be listening to connections on localhost by default.  POst your /etc/mysql/my.cnf.

---

### Post by TheDanMan on 2005-09-06
Sounds more like his loopback interface isn't up.  Run ifconfig and post the results.  If you don't get a block that says something like:

> 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:578586 (565.0 KiB)  TX bytes:578586 (565.0 KiB)
 

Then try running as root or sudo:
> 
ifconfig lo up 127.0.0. netmask 255.0.0.0

I don't think you actually have to declare the netmask but it won't hurt.

---

### Post by lao_V on 2005-09-08
you should use something like

 ```
mysql -u user -h localhost -p
``` 

avoid using local IP (127.0.0.1) as mysql doesn't recognise it as being same as localhost. It only goes by what's in the privileges table for the user and you won't see an entry for 127.0.0.1 by default

---

