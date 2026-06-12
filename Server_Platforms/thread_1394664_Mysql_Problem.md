---
title: "Mysql Problem?"
date: 2010-01-30
forum: Server Platforms
---

### Post by markinf on 2010-01-30
I put my mysql server to listen to my "network" ip, but there's a problem I only get the network IP when I join the network, which happens on networkmanager in DE, however I put mysqld to start on "boot" time (sysv) here on Ubuntu.

So I'm getting the ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2), which is kinda obvious since I'm not attached to the network. So what happens is that everytime I need to use mysql I do first a "restart" to get the daemon to work. And then everything works fine.

However, is there any "workaround" for this little problem?

---

### Post by amsterdamharu on 2010-01-30
What's in your /etc/hosts file? Are they different when you're connected and when you're not connected.

It should have something like this:

127.0.0.1       localhost

[update]
Maybe this helps:
[http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.1/en/can-not-connect-to-server.html)
Do you need to connect to the server from another computer? If not then use "bind-address     = 127.0.0.1" if you do then comment out that line (if it's there).

---

