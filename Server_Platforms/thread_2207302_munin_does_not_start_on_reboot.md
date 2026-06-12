---
title: "munin does not start on reboot"
date: 2014-02-23
forum: Server Platforms
---

### Post by bobptz on 2014-02-23
munin works only after I start it manually:  service munin-node start

If I reboot the server, munin graphs do not update.

I tried this:
```
$ update-rc.d munin-node defaults
update-rc.d: warning: /etc/init.d/munin-node missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/munin-node ...
   /etc/rc0.d/K20munin-node -> ../init.d/munin-node
   /etc/rc1.d/K20munin-node -> ../init.d/munin-node
   /etc/rc6.d/K20munin-node -> ../init.d/munin-node
   /etc/rc2.d/S20munin-node -> ../init.d/munin-node
   /etc/rc3.d/S20munin-node -> ../init.d/munin-node
   /etc/rc4.d/S20munin-node -> ../init.d/munin-node
   /etc/rc5.d/S20munin-node -> ../init.d/munin-node
```

It did not help.

Could this be a problem?
```
update-rc.d: warning: /etc/init.d/munin-node missing LSB information
```

```
root@server1:~# initctl show-config -e munin-node
munin-node
  start on filesystem (job:, env:)
  start on net-device-up (job:, env: IFACE=lo)
  stop on runlevel (job:, env: [!2345])
```


ubuntu 12.04 server
nginx 1.4.4
[I][Munin]("http://munin-monitoring.org/") version 1.4.6

[/I]

---

