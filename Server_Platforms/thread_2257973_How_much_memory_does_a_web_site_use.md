---
title: "How much memory does a web site use?"
date: 2014-12-23
forum: Server Platforms
---

### Post by RavenLX on 2014-12-23
I have a server (v. 10.04 until I can get time to get a 14.04 running) which hosts several domains on the same server. I want to find a way to see how much memory a domain is taking up. Sorta like phptop but I don't want to use phptop becuase it won't run as a cron job. If I use top it only shows how much memory an apache process is taking but it doesn't show me what domain that process is referring to. Anyone know of a tool that can help with this?

---

### Post by TheFu on 2014-12-24
It doesn't really work that way.
Traffic, any external dependencies and the language used for the website/static content matter more.  The best recommendation is to setup system-wide performance monitoring and watch how that changes over a month, a year.  That will give you a better idea how things work as a single new vhost is added.

---

### Post by SeijiSensei on 2014-12-24
> **RavenLX said:**
> If I use top it only shows how much memory an apache process is taking but it doesn't show me what domain that process is referring to. Anyone know of a tool that can help with this?
The Apache listener processes are not tied to a specific virtual host.  They simply accept inbound requests and respond accordingly depending on the URL.  Most listeners on my server use from 9-40 MB of memory per instance.  This machine has 2G of memory and handles other tasks as well, but still has a lot of free memory.

---

### Post by RavenLX on 2014-12-24
I see. I don't know how phptop is doing it then. I looked at the code and was confused. Thanks for all the advice. I think I agree that other approaches might be more appropriate.

---

### Post by MAFoElffen on 2014-12-24
Other factors... RAM is a factor... memory used by a Web Host domain becomes a factor when how much server side scripts and applications are using on the server side of the site. A rule of thumb limit for a lot of web hosting services is a 500MB limit on each site. Above that, they charge more. It usually has to be some fairly large, complex scripts to breach that limit. More of a factor is CPU, dB connections and throughput. Unless my thinking on that is mis-guided... that is just what I've found so far.

---

### Post by TheFu on 2014-12-27
I've seen webservers with 3000 virtualhosts, but next to no traffic.
And i've seen single websites with 200 servers being load balanced.

Until you capture the performance stats for THIS PARTICULAR SERVER, we don't know anything.

---

