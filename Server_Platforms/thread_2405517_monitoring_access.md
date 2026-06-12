---
title: "monitoring access"
date: 2018-11-07
forum: Server Platforms
---

### Post by ngongoloy on 2018-11-07
hai, 

sorry am a newbie n ubuntu. i hv aquestion, is it possible to monitor our webserver (apache2)  traffic ( I mean an IP that access/open the webserver from public)? or need more tool to install?

---

### Post by mastablasta on 2018-11-07
there are plenty of tools. maybe look at munin or monitorix for example. Nagios Core is also good and has plenty of forks (e.g. Naemon) as well as plugins.

here is a nice selection with short description: [https://blog.serverdensity.com/80-linux-monitoring-tools-know/](https://blog.serverdensity.com/80-linux-monitoring-tools-know/)
and another one here: [https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/](https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/)

---

### Post by howefield on 2018-11-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by TheFu on 2018-11-08
Welcome to the forums.

If you want to monitor specific pages visited by different IPs, then you want something called "web analytics."  I've used Webalizer and AWStats, but there are many. They all require manual configuration. They work by monitoring the web-server logs.  If you add a small javascript instrument to all your pages, you can get much more detailed client-side data like screen resolutions, and many hardware related thing. It is actually pretty scary the details available. 

You can even allow google to provide analytics, at the price of all your data and the privacy of your visitors.  Many webmasters do this.

You can find more options by using **AWStats vs** as a search term.

---

