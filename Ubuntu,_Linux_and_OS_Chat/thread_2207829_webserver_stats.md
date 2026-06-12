---
title: "webserver stats"
date: 2014-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by Tommy_Maersk on 2014-02-25
Hey
I run an ubuntu webserver, with a bunch of domains hosted on it.

Now i want to see some stats on it, like how many visits to this and that domain etc.

I tryed with webalizer, but that didnt really show stats for each individual domain?

Anyone got some interesting input on this?

Thanks

---

### Post by TheFu on 2014-02-25
You'd have to setup webalizer for each domain if each on writes to a different weblog.  If the weblogs are merged into a single file, I'd think the stats would be merged too.  We use awstats ... on a per-domain basis. It is similar to webalizer.

Or ... you could setup a reverse proxy as a front-end to all the virtual-domains and run the statistics against that front-end traffic from a single logfile. nginx can do this though you'll need tweak the logfile parser.  Plus nginx is much faster than most other webservers.  Apache can probably do the same stuff with a reverse proxy.

Does this help?

---

### Post by Lars Noodén on 2014-02-25
Do all your name-based virtual host configuration files point to the same log files or to different ones?   If you have left them as default they will all dump into the same location and you won't be able to sort them out.  So be sure that [ErrorLog](http://httpd.apache.org/docs/2.4/mod/core.html#errorlog) and [CustomLog](http://httpd.apache.org/docs/2.4/mod/mod_log_config.html#customlog) are pointing to a unique pair of files for each vhost.

---

### Post by Tommy_Maersk on 2014-02-25
Ahh yes okay, think I understand now, right now all the log entries goes to the same file the error.log and access.log, need to create a seperate one for each domain and set it up in the virtualhosts file for each domain, and then tell webalizer to read that specific log file right?

---

