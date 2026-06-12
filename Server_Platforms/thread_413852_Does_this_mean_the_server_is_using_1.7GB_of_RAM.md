---
title: "Does this mean the server is using 1.7GB of RAM?"
date: 2007-04-19
forum: Server Platforms
---

### Post by ade234uk on 2007-04-19
Or am I looking at this wrong way around?

Mem:   1943904k total,  1752944k used,   190960k free,   192712k buffers
Swap:   530104k total,      116k used,   529988k free,   508436k cached

---

### Post by dfreer on 2007-04-19
Try using htop instead of top for accurate memory usage (from CLI):
```
sudo apt-get install htop
```
If you have a GUI with Gnome use System Monitor:
System > Administration > System Monitor.

See this thread about why top reports different memory usage from System monitor/htop:
[http://ubuntuforums.org/showthread.php?t=393176](http://ubuntuforums.org/showthread.php?t=393176)

EDIT: My web server typically uses around 54 MB's of RAM. woot!

---

