---
title: "Run several instance of ulog"
date: 2012-10-02
forum: Server Platforms
---

### Post by g1franc on 2012-10-02
Hello,

I'm trying to run several instance of ulogd on the same server, each one having a different configuration. 
My goal is to use ulog groups to have several kind of logging facilities:
* one only using syslogemu
* one for mysql
* etc.....

Because I want some lines to be put only into mysql, some only on files and so on...

From  what I read from the documentation, I have to run several instance,  each one with a different configuration file, specifying a different  "nlgroup".

Unfortunately, I can't manage to handle the daemon several times through the Ubuntu **init.d** script.

I tried to duplicate the **init.d** script of the original ulogd package to spawn several instances and manage them through each dedicated script, but each script seem to point to the same ulogd "instance".

I also tried to use the /etc/init.d/skeleton, by duplicating it and adapt it, as it make use of **--pidfile** to match the processes.

I even try to specify **-m** argument of **start-stop-daemon** to force the creation of the PID file but it was never created.

Does anyone have a clue on how to do this ?

Regards.

---

