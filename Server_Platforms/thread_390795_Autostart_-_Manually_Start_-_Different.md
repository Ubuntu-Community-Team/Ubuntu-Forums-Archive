---
title: "Autostart - Manually Start - Different??"
date: 2007-03-22
forum: Server Platforms
---

### Post by hblaw on 2007-03-22
I placed a service (mindquarry) script in /etc/init.d/mindquarry, and used update-rc.d to add it to defaults.

Weird things happen:

1. I can run /etc/init.d/mindquarry start to start the service manually and everything works fine.
2. With auto start at boot, the service is up and running (it is a web application), but I cannot log in in the web application (guess the service cannot access some files).
3. With auto start at boot, after I stop the service and then mannually start the service again, everthing works fine again.

Is anyone here know the difference (in accessing files, in particular) between manually start the service and auto start at boot? (use ps -ef | grep service_name) I found that both situations the same user is running the service.

I am in Dapper. Any clue?

best regards,
hb

---

