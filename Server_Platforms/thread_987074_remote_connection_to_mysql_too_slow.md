---
title: "remote connection to mysql too slow"
date: 2008-11-19
forum: Server Platforms
---

### Post by hctopcu on 2008-11-19
This is my first linux server. I'm very inexperienced.
I had a computer, windows and mysql installed. I had no problems with connecting remotely through other servers to mysql.
I want to use that machine for my vBulletin forums mysql server.
I installed ubuntu server. only openSSH and mysql.
Using >mysql through ssh is fast enough but when I connect remotely with php it takes over 6 to 17 seconds just to mysql_connect(). selecting db and executing queries fast enough.
I also try Query analyser tool and php script on wamp with a notebook. they're all slow on connect.

---

### Post by cdenley on 2008-11-19
> **hctopcu said:**
> This is my first linux server. I'm very inexperienced.
I had a computer, windows and mysql installed. I had no problems with connecting remotely through other servers to mysql.
I want to use that machine for my vBulletin forums mysql server.
I installed ubuntu server. only openSSH and mysql.
Using >mysql through ssh is fast enough but when I connect remotely with php it takes over 6 to 17 seconds just to mysql_connect(). selecting db and executing queries fast enough.
I also try Query analyser tool and php script on wamp with a notebook. they're all slow on connect.

I think I've had problem before where the server was trying to resolve the hostname of the client. Try adding an entry for your client in the /etc/hosts file on the server.

---

### Post by hctopcu on 2008-11-20
I added in the hosts but nothing changed.
I took a my.conf from vBulletin support forums given on a request for a machine; and the problem was gone. I couldn't find the exact problem but for now its ok. I must immediately learn how to modify and fine tune my.conf I guess.
Its very strange to me that the default my.conf could cause that kind of error.
Thank you.

---

### Post by Roger_Smith on 2008-11-20
More than likely the new my.cnf disables the DNS lookups that MySQL does for host lookups.  You can check this out by looking at your my.cnf for the following:

```

skip-name-resolve
skip-host-cach
```

This prevents MySQL looking up Hostnames for IP addresses.

---

