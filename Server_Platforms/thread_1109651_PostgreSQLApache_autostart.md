---
title: "PostgreSQL/Apache autostart"
date: 2009-03-29
forum: Server Platforms
---

### Post by swraman on 2009-03-29
Hi,

I currently have PostgreSQl and apache both running on my Ubuntu machine.

Currently, Pgsql autostarts, and it sometimes adds a whole minute to the startup time.  How can I stop it from starting up when the computer starts up?

conversley, is there any way to get apache to autostart when I boot Ubuntu?

Thanks

---

### Post by windependence on 2009-03-30
There should be  symlinks in /etc/rc3.d  and  /etc/rc5.d (or whatever runlevel it starts in) pointing to /etc/init.d/postgresql  (so  that the boot sequence runs  /etc/init.d/postgresql start for you --- so to speak)

These symlinks should be named SXXpostgresql  (where XX is a two-digit
code that indicates the order in which the service is started.

You'll need to comment out those lines to stop it from starting on boot, but I have to say that I have a fair amount of experience with PG, and it should not take that long to start.

Apache is started in much the same way, or in some cases you can add the "apachectl start" command to the /etc/rc.local file, if that functionality exists in Ubuntu, I'm not really sure. I like to start my databases in rc.local because all the other services such as network have started by the time that step is reached in the boot process. This is the way it's done in Red Hat based distros but I am not sure if Ubuntu allows this.

-Tim

---

