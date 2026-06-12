---
title: "web log analysis"
date: 2008-09-06
forum: Server Platforms
---

### Post by aba3k on 2008-09-06
Hi

I'm searching a way to see my logs in a web interface.
Anyone know of projects to make this?

---

### Post by Paul41 on 2008-09-06
If doesn't have to be web based I have heard good things about AWStats. I have never tired this but it is open source and sounds really nice.

[http://awstats.sourceforge.net/](http://awstats.sourceforge.net/)

I don't know of a way to view the log files with anything web based. If you are looking for visitor stats Piwik is web based (it's similar to Google Analytics). It is open source and it stores all it's information on your server and database.

[http://piwik.org/](http://piwik.org/)

---

### Post by aba3k on 2008-09-06
> **Paul41 said:**
> If doesn't have to be web based I have heard good things about AWStats. I have never tired this but it is open source and sounds really nice.

[http://awstats.sourceforge.net/](http://awstats.sourceforge.net/)

I don't know of a way to view the log files with anything web based. If you are looking for visitor stats Piwik is web based (it's similar to Google Analytics). It is open source and it stores all it's information on your server and database.

[http://piwik.org/](http://piwik.org/)

It' something like awstats, but for generic log messages (like auth.log, messages.log squid.log etc). Something that generate graphics, like rrd graphs, for proxy usage, server status, network stats, bandwidth usage etc. 
Looking now, the title is a bit wrong.

Thanks.

---

### Post by schettj on 2008-09-07
> **aba3k said:**
> It' something like awstats, but for generic log messages (like auth.log, messages.log squid.log etc). Something that generate graphics, like rrd graphs, for proxy usage, server status, network stats, bandwidth usage etc. 
Looking now, the title is a bit wrong.

Thanks.
Munin can do all that. You may have to write some plugins but its easy enough to do.

[http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html](http://www.ubuntugeek.com/monitoring-servers-and-clients-using-munin-in-ubuntu.html)

---

