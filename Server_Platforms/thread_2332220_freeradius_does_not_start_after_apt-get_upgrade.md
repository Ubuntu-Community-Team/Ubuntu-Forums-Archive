---
title: "freeradius does not start after apt-get upgrade"
date: 2016-07-29
forum: Server Platforms
---

### Post by mmiranda75 on 2016-07-29
Hello to all, i have a ubuntu server 14.04 that i update it using apt-get update/upgrade on regular basis, i had to reboot the server today and now freeradius does not start automatically, i foud this error in syslog:

Jul 29 09:13:34 appsrv01 kernel: [   34.920410] init: freeradius main process (1642) terminated with status 1
Jul 29 09:13:34 appsrv01 kernel: [   34.920433] init: freeradius main process ended, respawning
Jul 29 09:13:34 appsrv01 kernel: [   35.339768] init: freeradius main process (1646) terminated with status 1
Jul 29 09:13:34 appsrv01 kernel: [   35.339790] init: freeradius main process ended, respawning
Jul 29 09:13:34 appsrv01 kernel: [   35.696426] init: freeradius main process (1692) terminated with status 1
Jul 29 09:13:34 appsrv01 kernel: [   35.696448] init: freeradius respawning too fast, stopped


freeradius starts fine when running /etc/init.d/freeradius start command.
Investigating i found that i have a file in /etc/init.d/freeradius and another one in /etc/init/freeradius.conf, i don't know if this is causing the probem, may be in previus apt-get upgrade the system messed up the hole init system and im noticing it just now that a rebooted the server, what file should i leave?

---

