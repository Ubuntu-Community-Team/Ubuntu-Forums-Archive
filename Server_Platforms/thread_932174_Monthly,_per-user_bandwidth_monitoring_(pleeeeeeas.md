---
title: "Monthly, per-user bandwidth monitoring (pleeeeeease?!)"
date: 2008-09-28
forum: Server Platforms
---

### Post by evilspoons on 2008-09-28
I have asked this question a few times and done a million Google searches but I've never come up with a solution, so I'm going to ask here again.

Does anyone know of a software package I can run on my Ubuntu server that will track my per-calendar-month bandwidth usage and break it down on a per-user basis?

I used to use Smoothwall but then moved up to Ubuntu Server when I had a large number of files I needed to share, etc. Smoothwall had a mod called [Bandwidth Usage Viewer]("http://community.smoothwall.org/forum/viewtopic.php?t=5393"). It sets up an ipac cron job of some sort and then interprets the data it gets from ipac in a Perl script. I barely-if-at-all understand ipac and I do not know Perl so my success in reverse-engineering Bandwidth Usage Viewer to implement on Ubuntu has been zero.

Bandwidth Usage Viewer allows you to set:
1. the anniversary date your monthly bandwidth allowance resets
2. what your monthly bandwidth allowance is
3. IPs on your network to monitor specifically
4. what proportion of bandwidth each IP is allowed to use

It then generates plots (bar graphs) that show the percentage of the bandwidth you've used, and the percentage of allocated bandwidth each IP has used. Anyone on the network can then open a web page on the server and see the statistics.

It also ***only*** counts bandwidth from each IP on the local (internal network) interface crossing in or out through the remote (internet connection) network interface, to prevent the data from a user copying a file to the server or to another local computer being added to their monthly usage totals.

It looks like this:

[IMG]http://members.shaw.ca/slipstream3d/bv061-1.PNG[/IMG]

Before anyone says "100 GB is a lot", "just use DD-WRT", or anything else saying I really don't think I need this tool, please don't bother. I have a limited-bandwidth connection shared with several others who love to download hundreds of gigabytes of crap and then claim that it wasn't **them** who hit our monthly bandwidth cap two weeks into the month. This makes using a standalone router like a Linksys WRT54G impossible because of all the open connections it has to handle, and all of the bloody storage it has to maintain (1.8 TB and counting.)

I have been searching for something like this for *years* now and any insight would be **immensely** appreciated.

---

### Post by Vishal Agarwal on 2008-09-28
Pls see the attached file guiding, how to install the awstats. Awstats is a web based tool which works with squid proxy server and keeps the record of every ip and the band width used. It will show you the daily,weekly,monthly and yearly usage of every IP. you will need to change the squid proxy log setting to "Use HTTPD log format ?"to yes. This I have done through the webmin interface. Alternatively you can assign a limited bandwidth and a limited Download size to every IP, using the webmin interface. Although I have not done this much of deep exercise but I know that it is possible.

[See this URL]("http://pcquest.ciol.com/content/search/showarticle.asp?arid=74686&way=search")

---

### Post by mindoms on 2008-09-28
The README on this page seems to be helpfull
[http://www.daneben.de/ipac.html](http://www.daneben.de/ipac.html)

hth, stefan

---

