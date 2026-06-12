---
title: "Squid &quot;parent directory must be writeable&quot;"
date: 2010-07-05
forum: Server Platforms
---

### Post by inyoka on 2010-07-05
Hi,

Running "start squid" starts the daemon with apparently no problems, however syslog gives the following message :

```
Jul  6 09:48:28 ltsp squid[2273]: Cannot open '/var/log/squid/access.log' for writing.#012#011The parent directory must be writeable by the#012#011user 'squid', which is the cache_effective_user#012#011set in squid.conf.
Jul  6 09:48:28 ltsp squid[2262]: Squid Parent: child process 2273 exited due to signal 6
Jul  6 09:48:28 ltsp squid[2262]: Exiting due to repeated, frequent failures
Jul  6 09:48:28 ltsp init: squid main process (2262) terminated with status 1
```

These are the permissions on the directory which appear correct :

```
drw-rw-r--  2 squid squid 4096 2010-07-05 16:09 .
drwxr-xr-x 17 root  root  4096 2010-07-06 09:17 ..
-rw-rw-r--  1 squid squid    0 2010-07-05 16:07 access.log
-rw-rw-r--  1 squid squid 9270 2010-07-05 16:09 cache.log
```

These are my cache effective settings in squid.conf : 

```
cache_effective_user squid
cache_effective_group squid
```


Software :
Ubuntu v. 10.04, Squid v. 2.7.STABLE7-1ubuntu12

Any ideas?

---

### Post by upbeat.linux on 2010-07-06
Try

```
sudo chown -R squid:squid /var/log/squid
sudo chmod 755 /var/log/squid

```

then restart squid:

```
sudo /etc/init.d/squid restart
```

---

