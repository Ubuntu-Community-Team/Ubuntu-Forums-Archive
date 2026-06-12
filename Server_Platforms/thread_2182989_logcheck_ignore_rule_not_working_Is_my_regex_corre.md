---
title: "logcheck ignore rule not working? Is my regex correct?"
date: 2013-10-23
forum: Server Platforms
---

### Post by talz13 on 2013-10-23
I've started using logcheck to keep up on any out-of-the-ordinary events on my server.  I'm down to only a couple notifications that I want to filter away, but one of them just won't stay quiet!

I keep getting this notification:
```
Oct 23 06:41:56 server dbus[1167]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Oct 23 06:41:57 server dbus[1167]: [system] Successfully activated service 'org.freedesktop.PackageKit'
```

This is my ignore rule in /etc/logcheck/ignore.d.server/syslogd:
```
^\w{3} [ :0-9]{11} [._[:alnum:]-]+ dbus\[[0-9]+\].*.service.*.\'org.freedesktop.PackageKit\'.*$
```

When I check each of the sample log lines against my ignore rule on [http://www.myregextester.com/](http://www.myregextester.com/) it matches both of them.

What could the problem be?

---

