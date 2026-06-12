---
title: "apache status parameter doesn't work"
date: 2009-07-10
forum: Server Platforms
---

### Post by bashir1364 on 2009-07-10
I can't see the status of my apache2 service,

I type this:

```
 sudo /etc/init.d/apache2 status
```

and the output is:

```
 * Usage: /etc/init.d/apache2 {start|stop|restart|reload|force-reload|start-htcacheclean|stop-htcacheclean}
```

---

### Post by slugmax on 2009-07-10
What version of Ubuntu is this? I don't recall the status option missing from the apache init file, but maybe it was in older versions (I have it in my 9.04). You can mimic it with a bit of Perl:

```

ps axj | perl -nle 'print "* Apache is running (pid $1)." if /^\s+1\s+(\d+).+?apache2/'

```

This relies on the 'j' switch to ps, which prints the parent PID in the first column and the PID in the second column. The parent PID of the main Apache process is always 1. You don't need sudo with this (or the /etc/init.d/apache2 status, if you had it). Just as with the real status, it will print nothing if no parent apache2 process is running.

---

