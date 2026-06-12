---
title: "ntop/Nmon alternatives"
date: 2007-12-16
forum: Server Platforms
---

### Post by satimis on 2007-12-16
Hi folks,



Any folk has experience on ntop/Nmon


[http://www.ntop.org/overview.html](http://www.ntop.org/overview.html)
and its spinoff NMON
[http://www.nmon.net/index.html](http://www.nmon.net/index.html)


Nmon
[http://en.wikipedia.org/wiki/Nmon](http://en.wikipedia.org/wiki/Nmon)


nmon for AIX and Linux Performance Monitoring
[http://www-941.ibm.com/collaboration/wiki/display/WikiPtype/nmon](http://www-941.ibm.com/collaboration/wiki/display/WikiPtype/nmon)


A free tool to analyze AIX and Linux performance
[http://www.ibm.com/developerworks/aix/library/au-analyze_aix/index.html](http://www.ibm.com/developerworks/aix/library/au-analyze_aix/index.html)


Please shed me some light.  Are there better alternatives on server/network monitoring ?  TIA


B.R.
satimis

---

### Post by gritsul on 2008-03-15
nmon is an Ideal tool for performance monitoring.
You can Install nmon on Ubuntu following this link:
[COLOR="Lime"]
[http://rgritsulyak.blogspot.com/2008/03/memory-usage-on-ubuntu-development.html]("http://rgritsulyak.blogspot.com/2008/03/memory-usage-on-ubuntu-development.html")
[/COLOR] and using instruction presented there.
Also you can use hand written scripts, use output of ```
ps -eaux 
``` , grep'ed by interesting for you process.

In ubuntu, there is also top command, that can be used as basic tool for process monitoring.

---

### Post by satimis on 2008-03-15
> **gritsul said:**
> nmon is an Ideal tool for performance monitoring.
You can Install nmon on Ubuntu following this link:
[COLOR="Lime"]
[http://rgritsulyak.blogspot.com/2008/03/memory-usage-on-ubuntu-development.html]("http://rgritsulyak.blogspot.com/2008/03/memory-usage-on-ubuntu-development.html")
[/COLOR] and using instruction presented there.
Also you can use hand written scripts, use output of ```
ps -eaux 
``` , grep'ed by interesting for you process.

In ubuntu, there is also top command, that can be used as basic tool for process monitoring.
Thanks for your advice.


I'm running Ubuntu 7.04 server amd64.  I found "nmon4linux_x86_64_b.zip" on;

[http://www-941.ibm.com/collaboration/wiki/display/WikiPtype/nmon](http://www-941.ibm.com/collaboration/wiki/display/WikiPtype/nmon)

But it is an exprimental version.  Any idea?


TIA


satimis

---

