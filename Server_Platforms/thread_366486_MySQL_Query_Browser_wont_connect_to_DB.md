---
title: "MySQL Query Browser wont connect to DB"
date: 2007-02-20
forum: Server Platforms
---

### Post by azazel00 on 2007-02-20
Hey gents,

I was having a problem with the mysql admin program. It crashed everytime I tried to fetch the users panel.

Anyway, a friend told me to upgrade the admin because the most recent version didnt have the mentioned problem. I went to mysql.com, downloaded the gui-tools (which aparently they decided not to port to a .deb package... shame on them), the I extracted it to the /opt/ folder since it failed to launch from any othe location.

Long-story short, MySQL Admin works great after I fixed the Menu launchers to point to it. MySQL Query Browser, on the other hand, is trying to use the default socket location: '/tmp/mysql.sock'

I checked my /etc/mysql/my.cnf, and the client section lists the appropriate socket.
```
#
...
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock
...

```

So the question:
How on earth do I make the Query Browser read the my.cnf file? I know that I can hit 'details' and specify the socket. I am also guessing that it could copy the mysql.socket to the folder it is trying to use, but I'm not looking for temporary workarounds. I'd like it to read the configuration properly. Or alternatively, fix the configuration file it is reading (If anyone can tell me where that is).

Regards,
az

---

