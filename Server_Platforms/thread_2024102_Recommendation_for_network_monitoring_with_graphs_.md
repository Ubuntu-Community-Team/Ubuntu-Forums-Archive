---
title: "Recommendation for network monitoring with graphs from headless server"
date: 2012-07-13
forum: Server Platforms
---

### Post by bpb_21 on 2012-07-13
Here's my situation; hope someone can help.

I inherited a SOHO network that I'm now in charge of.  I'd like to monitor the network using Ubuntu server 12.04 (headless) that I've set up.  My issue is that I need to be able to produce charts/graphs that humans can understand (i.e. - that I can show to the non-technical people - specifically everyone else - in the organization) to show what's going on with the network.

I have Windows Server 2008 R2, a Netopia router, and five Cisco SPA504G VoIP phones that I need to monitor.  I need to monitor them using the ubuntu server, which means I need some application that can produce graphs and display them somewhere like on a webpage, rather than directly on an attached display.

I've set up Munin and it works great for the ubuntu server, windows server and netopia.  It does just what I need.  The problem is, those three devices use SNMP with Munin just fine and the Cisco SPA504G VoIP phones, of course, do not support SNMP.  I'd like to have one application to monitor all of this stuff, rather than several.

I've looked at syslog-ng; the setup & configuration documentation isn't user-friendly if you don't already know how to set up and configure syslog-ng (which seems a little pointless to me).  I've also looked at nxlog ([http://nxlog-ce.sourceforge.net/"]("http://nxlog-ce.sourceforge.net/")) but I'm not sure if it co-exists with Munin (attempting to install the .deb package for it uninstalls at least one "munin" package in the process) and I'm not ready to jump ship on Munin just yet.

Is there a syslog or xml plug-in for Munin, specifically with the Cisco SPA504G (the phones do support syslog and xml formats), that I might have overlooked?  I haven't found one in my internet searches just yet.

Is there any clearer documentation for syslog-ng than this?
[http://www.balabit.com/sites/default/files/documents/syslog-ng-ose-3.3-guides/syslog-ng-ose-v3.3-guide-admin-en.html/index.html-single.html]("http://www.balabit.com/sites/default/files/documents/syslog-ng-ose-3.3-guides/syslog-ng-ose-v3.3-guide-admin-en.html/index.html-single.html")
Or do I just need to spend a little more time with syslog-ng?  It seems like there is an add-on to produce graphs, using php-syslog-ng or something similar.

Also, has anyone used nxlog?  It seems a little easier to implement than syslog-ng, but I'd like a recommendation before I waste any more time installing something new from scratch.

Thanks for any help/advice!  Oh yeah, my budget is $0.00 for this project - one of the "perks" for working with a non-profit!

---

### Post by Cheesemill on 2012-07-13
For graphing data that you have already collected then you would probably use [RRDtool]("http://oss.oetiker.ch/rrdtool/").

If you are looking to monitor your IT infrastructure then [Nagios]("http://www.nagios.org/") or [Cacti]("http://www.cacti.net/") are probably the applications to look at (both of these use RRD to graph their data).

LHammonds has written a brilliant Nagios tutorial on this site:
[http://ubuntuforums.org/showthread.php?t=1986743](http://ubuntuforums.org/showthread.php?t=1986743)

---

### Post by bpb_21 on 2012-07-13
Thanks for the info - I'm definitely going to check out the Nagios tutorial, as it should complement Munin (and hopefully pull in monitoring for those VoIP phones...)

---

### Post by bpb_21 on 2012-07-17
> **Cheesemill said:**
> For graphing data that you have already collected then you would probably use [RRDtool]("http://oss.oetiker.ch/rrdtool/").

If you are looking to monitor your IT infrastructure then [Nagios]("http://www.nagios.org/") or [Cacti]("http://www.cacti.net/") are probably the applications to look at (both of these use RRD to graph their data).

LHammonds has written a brilliant Nagios tutorial on this site:
[http://ubuntuforums.org/showthread.php?t=1986743](http://ubuntuforums.org/showthread.php?t=1986743)

Thanks for all that; Nagios is up and running along with Munin and MRTG.  The only problem I'm having is that I can't seem to get any meaningful data from the SPA504G VoIP phones.  I'll probably have to write a plugin for nagios.  Either that, or buy a Cisco PBX...

---

### Post by psyllex on 2012-12-31
> **bpb_21 said:**
> Thanks for all that; Nagios is up and running along with Munin and MRTG.  The only problem I'm having is that I can't seem to get any meaningful data from the SPA504G VoIP phones.  I'll probably have to write a plugin for nagios.  Either that, or buy a Cisco PBX...

How did you do getting Nagios up and running? I'm having issues getting it running properly.  I have it running now but it says my server is down; yet I'm accessing my server from another machine through it's IP address so I'm not certain how Nagios is registering it down.  I've had to mix and match instructions just to get it running.  The last set of instructions a person from Nagios' site sent me was missing about 5-6 steps that I had to fetch off another person's site.  So I'm not entirely sure it's set up right.  I've attempted to remove nagios but it freaks out because it's in 3 different directories all spread out some in /etc some in /usr.  I'm thinking of just reinstalling my server software and starting fresh.  Do you have any suggestions or hints?

---

