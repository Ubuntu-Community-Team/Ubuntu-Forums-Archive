---
title: "BoxBackup Server Daemon not starting"
date: 2011-07-27
forum: Server Platforms
---

### Post by sirgogo on 2011-07-27
Hi all-

I'm trying to run BoxBackup to sync a couple active servers to a data server. I installed the server and client, making sure to follow the instructions closely with all the certificates. The problem is the service daemon on the service won't even start. The service manage reports: "bbstored dead but pid file exists" (basically, tried to instantiate the process, but it died due to faults).

Here's the log of the daemon in /var/log/box

```
Jul 27 13:05:10 frogbert bbstored[13429]: NOTICE: Box Backup Store Server v0.11rc8, (c) Ben Summers and contributors 2003-2010
Jul 27 13:05:10 frogbert bbstored[13433]: NOTICE: Starting daemon, version: 0.11rc8
Jul 27 13:05:10 frogbert bbstored[13433]: NOTICE: Using configuration file: /etc/boxbackup/bbstored.conf
Jul 27 13:05:10 frogbert bbstored[13433]: WARNING: Exception thrown: ServerException(SocketBindError) at ../../lib/server/SocketListen.h(232)
Jul 27 13:05:10 frogbert bbstored[13433]: FATAL: Terminating due to exception Server SocketBindError (Check the ListenAddresses directive in your config file -- must refer to local IP addresses only) (3/16)
Jul 27 13:05:10 frogbert bbstored/hk[13434]: NOTICE: Terminating daemon
```

The error code (3/16) is listed on their [website]("http://www.boxbackup.org/trac/wiki/Troubleshooting") to be a ListenAddresses directive in the bbstored.conf file.

This was my listed directive prior to any change:
```
ListenAddresses = inet:frogbert
``` (frogbert is the host).

So I changed it to ```
ListenAddresses = inet:192.168.42.100
``` to be entirely compliant with the network. Didn't work. I even tried 127.0.0.1 (localhost) and 0.0.0.0 (just for kicks), but still no luck.


Any ideas? Any advice or help would be greatly appreciated.

---

### Post by sirgogo on 2011-07-29
Solved it myself. httpd was blocking the port. Killed httpd and restarted bbstored. Worked great.

---

