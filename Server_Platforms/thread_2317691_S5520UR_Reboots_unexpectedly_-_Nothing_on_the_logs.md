---
title: "S5520UR Reboots unexpectedly - Nothing on the logs prior to rebbot"
date: 2016-03-18
forum: Server Platforms
---

### Post by ErnestoC on 2016-03-18
Hello,

I have a S5520UR server running with  Ubuntu 14.04.4 LTS (GNU/Linux 3.16.0-62-generic x86_64).

For (apparently) no reason the server reboots randomly and I can't find nothing on the logs prior to the reboots.

Does anyone know where could I search for the causes ?

There isn't any watchdog installed ...

Thanks !

Ernesto.

---

### Post by nerdtron on 2016-03-19
Which logs are you looking into (syslog, apache logs, mysql log, etc.)? What applications are running on the server?
Do you setup a cpu/ram/load monitoring on the server? This is valuable information in terms of monitoring the server performance especially prior to an unexpected reboot.

---

