---
title: "Network Performance Monitoring Software?"
date: 2007-10-19
forum: Server Platforms
---

### Post by stang on 2007-10-19
Hello I have been testing the Solar Winds Orion Network Performance Monitor software and was wondering if there is anything comparable that is open source that I can run on Ubuntu.  I basically need to see network traffic, which computer is spitting out the most traffic, errors, etc.  Thanks!

---

### Post by tkharris on 2007-10-19
tcpdump = good for checking things quicky
ethereal = good for longer tracking and parsing.

[http://www.tcpdump.org/](http://www.tcpdump.org/)
[http://www.ethereal.com/](http://www.ethereal.com/)

---

### Post by stang on 2007-10-31
Thanks but I'm talking about a program that lets me see the entire network, gives a chart of who is generating the most traffic, most errors, etc.

---

### Post by netlogic on 2007-10-31
You haven't said anything about any requirements, but ntop is what I use on servers with basic needs. It is lower on resource than others.

[http://www.ntop.org/overview.html](http://www.ntop.org/overview.html)

There are so many out there. It is basically based around your need.

---

### Post by NotRoot:-) on 2007-11-01
[http://oss.oetiker.ch/mrtg/](http://oss.oetiker.ch/mrtg/)
MRTG - The Multi Router Traffic Grapher
it is available in the Synaptic Package Manager

---

### Post by sean_evershed on 2007-11-06
Hi, I'm new to Ubuntu. I downloaded Nprobe from the NTOP web site but it's unclear to me how I actually install it after I have unzipped it. Can anyone please advise?

---

### Post by steve.horsley on 2007-11-07
It depends how you want to do the monitoring. 

MRTG is well known. It uses SNMP to poll routers or switches for interface statistics like send and received byte counts, and draws throughput graphs. You can also poll individual PCs of course if you install an SNMP daemon. I think OpenNMS has a similar capability.

ntop can produce interesting statistics, top talkers, top protocols etc. It can listen on a single network segment loke a protocol analyser, or you can use NetFlow probes like nprobe to send treffic reports to ntop. Many routers have netflow built in so they can report traffic stats to a netflow stats collector themselves. If you go for netflow, you'll find there are lots of FOSS netflow reporting products - use google for them.

---

### Post by agent8131 on 2007-11-08
The best monitoring program I've used is munin.  You can check out a site running it  here:

[http://munin.ping.uio.no/](http://munin.ping.uio.no/)

You can click on any host to get a flood of graphs.  Tou can click the graphs for more detail.  You can click the "day" "week" "month" "year" links to compare graphs of all the hosts (careful it's a lot of data).

---

### Post by wirelessmonkey on 2007-11-11
[www.groundworkopensource.com](www.groundworkopensource.com)
[www.opennms.org](www.opennms.org)
[www.cacti.net](www.cacti.net)
[www.zenoss.com](www.zenoss.com)

All these orgs have free applications, that run natively on linux, that have as much or more functionality than solar winds.

---

