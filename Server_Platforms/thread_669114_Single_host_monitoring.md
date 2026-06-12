---
title: "Single host monitoring"
date: 2008-01-16
forum: Server Platforms
---

### Post by Clashlab on 2008-01-16
Hello,

I am looking for a monitoring software for my (only) one Ubuntu 7.10 server.

It doesn’t have a lot of memory (128 MB) and I would like to be able to access as much characteristics as possible (CPU load, Memory usage, Temperature, Processes, Network load, Disk usage, …)  in graphs and all of that through a web page.

I found some really good software:
- Zenoss
- Nagios
- Zabbix
- Cacti
- Munin

But they are all for site monitoring (multiple servers), and some are very memory consuming.

So I need a piece of advise to choose between those or to find another one more suited to my needs.

Thx

---

### Post by jodeet on 2008-01-16
you seem to imply that you want the monitoring software to run on the one ubuntu server you have.  Note that the software you listed could be installed elsewhere, and be instructed to monitor your ubuntu box.

But if that's not what you want either, you might want to look into phpsysinfo:

[http://sourceforge.net/projects/phpsysinfo/](http://sourceforge.net/projects/phpsysinfo/)

which is a single php script that you can run via apache on your ubuntu box.  It will report stats just for that server.

---

### Post by Clashlab on 2008-01-16
Unfortunately I don't have another server that I can dedicate too monitoring.

Thanks for the link, it is near what I am looking for, except that there is no graph.

---

### Post by Clashlab on 2008-01-18
In between I found some other tools :
- MRTG
- Hyperic HQ
- GroundWork

But none is really what I was looking for. So I am testing Cacti and it seems great.
I choose it because it is under active development, it draws nice graph with easy change of scale and it seems to have a large community (so many templates to monitor a lot of things).

---

