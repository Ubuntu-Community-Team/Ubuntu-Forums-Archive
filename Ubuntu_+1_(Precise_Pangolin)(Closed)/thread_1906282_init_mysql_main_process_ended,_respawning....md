---
title: "init: mysql main process ended, respawning..."
date: 2012-01-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Krovas on 2012-01-08
```
[  501.198745] init: mysql main process (4542) terminated with status 1
[  501.198820] init: mysql main process ended, respawning
[  529.689853] init: mysql post-start process (4543) terminated with status 1
[  529.700598] type=1400 audit(1326074641.866:59): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=4668 comm="apparmor_parser"
[  530.990495] type=1400 audit(1326074643.155:60): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=4672 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=119 ouid=119
[  531.467695] init: mysql main process (4672) terminated with status 1
[  531.467782] init: mysql main process ended, respawning

```

A few minutes later...


```
[  743.224610] init: mysql main process (5598) terminated with status 1
[  743.224645] init: mysql main process ended, respawning
[  771.741289] init: mysql post-start process (5599) terminated with status 1
[  771.751280] type=1400 audit(1326074883.913:75): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=5727 comm="apparmor_parser"
[  772.950939] type=1400 audit(1326074885.113:76): apparmor="DENIED" operation="mknod" parent=1 profile="/usr/sbin/mysqld" name="/run/mysqld/mysqld.sock" pid=5731 comm="mysqld" requested_mask="c" denied_mask="c" fsuid=119 ouid=119
[  773.384324] init: mysql main process (5731) terminated with status 1
[  773.384357] init: mysql main process ended, respawning

```

This is happening over and over and over again every time I boot, which is brutalizing my hard drive and making starting up an excruciating experience. Would somebody please give me an idea of how to stop it?

Thank you.

---

