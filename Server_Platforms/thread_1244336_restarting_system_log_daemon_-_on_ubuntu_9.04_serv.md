---
title: "*restarting system log daemon - on ubuntu 9.04 server"
date: 2009-08-19
forum: Server Platforms
---

### Post by mrisolino on 2009-08-19
Hi guys!

Some days ago I upgraded my server and installed Webmin... Well, the next day when I turn on the monitor I see the msg on the screen "*restarting system log daemon" many times... and I dont know why...

I've looking for some info watching the logs... and i found that on /var/log/messages
```
Aug 19 08:00:01 serv-01 exiting on signal 15
Aug 19 08:00:01 serv-01 syslogd 1.5.0#5ubuntu3: restart.

```the restart is running hourly...

It is a CRON movement added by webmin maybe?

Thanks and sorry for my poor language....

---

### Post by mrisolino on 2009-08-21
I'm again...

I see that It's like a "tail" zombie... because i see, without loggin, some msgs from my logs...

When I login on server, I see 1 Zombie Process....
but when i type command top... he say 0 Zombies...

Please give me a hand :)

---

