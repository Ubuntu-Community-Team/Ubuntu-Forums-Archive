---
title: "Squid Unrecognized Service"
date: 2010-03-18
forum: Server Platforms
---

### Post by Mobadder on 2010-03-18
Dear all,
after compailing and make install,
i wanna to start squid
but unrecongnized service 
any idea,,
thanks in advance

---

### Post by cdenley on 2010-03-18
Undo everything you did, then:
```

sudo apt-get install squid

```

or if you want version 3.0
```

sudo apt-get install squid3

```

---

### Post by Mobadder on 2010-03-19
I do not wanna to install a pre-compilied squid, I need to compile and install it...Thanks

---

### Post by cdenley on 2010-03-19
> **Mobadder said:**
> I do not wanna to install a pre-compilied squid, I need to compile and install it...Thanks

Well then good luck, because software compiled yourself isn't supported by ubuntu, and I wouldn't want to install and maintain squid from scratch.

---

### Post by ant2ne on 2010-03-19
[http://www.ant2ne.com/?p=38]("http://www.ant2ne.com/?p=38")

---

### Post by Mobadder on 2010-03-22
Thx ant2ne,
when i excute /usr/local/squid/sbin/squid -z
the following error appears:
[COLOR="Red"]2010/03/22 18:08:43| Creating Swap Directories
FATAL: Failed to make swap directory /usr/local/squid/var/cache/00: (13) Permission denied
Squid Cache (Version 2.7.STABLE9): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0[/COLOR]
any idea,
thanks

---

### Post by firepage on 2010-12-01
Go to squid.conf and add the following line 
```
cache_effective_user squid
```

This line tells squid will be started under the user "squid"

Create the account if you have not and then change the ownership of the squid directory (including logs and cache) using the following command
```
# sudo chown -R squid /usr/local/squid/*
```

Create the cache directory using the following command
```
sudo /usr/local/squid/sbin/squid -z
```

And finally start squid
```
sudo /usr/local/squid/sbin/squid
```

Hope that helps

---

