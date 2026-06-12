---
title: "The best apache log analyzer?"
date: 2008-07-04
forum: Server Platforms
---

### Post by hearSAYkev on 2008-07-04
So I'm in search of a really good apache log analyzer. It doesn't have to be the greatest, but there's got to be something better than AWStats and Webalizer, right? Is there anything out there? Specifically in the repository, but I'm certainly willing to install it myself.

I looked into Splunk, but the free version's pretty locked down and I couldn't actually get it installed.

---

### Post by sjwk on 2008-07-04
Analog?  ([http://www.analog.cx/](http://www.analog.cx/))  Coupled with Report Magic perhaps..

Depends what you're wanting it to do I guess.  But analog is pretty widely used.

Steve.

---

### Post by windependence on 2008-07-04
I use webalizer.

-Tim

---

### Post by hearSAYkev on 2008-07-09
Looks like I'm going to try using AWStats with the JAWStats AJAX front-end (to make it pretty) [[http://www.jawstats.com]](http://www.jawstats.com])

As far as AWStats goes, does anyone know much about how (or even if) it handles multiple sites on the same server? Among other things, I'm most interested here in monitoring the bandwidth each site is using so I can determine at what point any of them might need to be moved to their own server.

---

### Post by hagen00 on 2008-07-09
bump...i would be very interested in some thoughts on this too, specifically monitoring specific domains Bandwidth use.

---

### Post by windependence on 2008-07-09
For bandwidth, I like MRTG, but the learning curve is a bit steep.

-Tim

---

### Post by Dr Small on 2008-07-09
> **windependence said:**
> I use webalizer.

-Tim
+1
I love Webalizer

---

### Post by Stephen_at on 2008-07-09
You can use awstats to monitor multiple sites on the same server by setting your apache config up so that each site goes into its own combined logfile and then setting up a configuation file for each site and then calling Awstats with the configuration passed as a parameter

---

### Post by mrtg.saitove.info on 2008-11-03
you can use "server-status" for apache and MRTG for some graphs

for example here is an output (its realtime):
> 

[https://xxx.xxx.xxx.xxx/server-status?auto:](https://xxx.xxx.xxx.xxx/server-status?auto:)

Total Accesses: 299
Total kBytes: 878
CPULoad: .321584
Uptime: 1844
ReqPerSec: .162148
BytesPerSec: 487.566
BytesPerReq: 3006.93
BusyWorkers: 1
IdleWorkers: 10


---

