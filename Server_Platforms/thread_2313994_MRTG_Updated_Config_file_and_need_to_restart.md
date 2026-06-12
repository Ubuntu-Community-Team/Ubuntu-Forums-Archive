---
title: "MRTG Updated Config file and need to restart"
date: 2016-02-17
forum: Server Platforms
---

### Post by rob158 on 2016-02-17
I have MRTG running on my machine by following standard automatic scripting, but I updated my config files and MRTG is not showing my changes.  How do I stop and restart MRTG?

---

### Post by sandyd on 2016-02-17
Moved to *Server Platforms*

---

### Post by MAFoElffen on 2016-02-17
> 
How do I stop and restart MRTG?

It is not a service, but rather an application the runs to it's end. So when you start it, it runs, then exits when it is finished... So you don't start, stop or restart like a service

So to test it, you start from the commandline
```

# syntax: mrtg mrtg.cfg <options>
sudo /usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok

```
^ Nottice that you need to tell it what config file to use, and where that is located...

Then when you have it tweaked how you want it to run, then add it to crontab, i.e.:
```

*/5 * * * * root LANG=C LC_ALL=C /usr/bin/mrtg /etc/mrtg/mrtg.cfg --lock-file /var/lock/mrtg/mrtg_l --confcache-file /var/lib/mrtg/mrtg.ok

```
Is that enough info to get you going?

---

