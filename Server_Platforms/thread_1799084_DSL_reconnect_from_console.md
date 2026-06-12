---
title: "DSL reconnect from console"
date: 2011-07-07
forum: Server Platforms
---

### Post by creiss on 2011-07-07
Hello all.

This is akward. I configured bind9, dhcp, tfp, apache et all with no problems. The server is serving around 80 perfectly fine-tuned linux clients (tho gentoo they are). All is well.

I am just failing at one point. I did set up Ubuntu's (11.04) Servers ppoeconf thingy, dsl is online. But umm...

what is the command to start, stop and restart the dsl connection? I honestly tried /etc/ppp/ip-{up,down}... No joy.

Again: It's working, dsl is up, but I like to reconnect by cron at a specific time of the day and I want to be able to force on/off the dsl line by web interface (which is also coded already).

Admin. Defeated by dsl reconnect command.

Help.


**Solved:** /sbin/ifup dsl-provider, /sbin/ifdown dsl-provider does the trick. Seems no one knew, tho :)

-Chris.

---

### Post by creiss on 2011-07-12
Seriously?

There is no reconnect to my dsl provider command?

Uhh...

---

