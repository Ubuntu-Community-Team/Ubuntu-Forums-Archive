---
title: "Server Monitoring tool?"
date: 2007-06-13
forum: Server Platforms
---

### Post by EvilMarshmallow on 2007-06-13
I have a windows server that runs a piece of software called "Servers Alive".  This is a server monitoring tool that polls our servers every couple of minutes to verify that they're still running.  It's really good because it can send me emails and/or pages when a system fails.

Is there a similar tool in the Ubuntu world?  I'd like to migrate and save myself some money on a Windows license if there's something like this I can use.

---

### Post by craigp84 on 2007-06-14
Hi EvilMarshmallow,

I can't think of anything identical to servers alive off the top of my head. However, it's still trivial to setup some kind of basic monitoring like that. Stick the following line in cron - adjust the times it runs and the server name checked:

Every 5 mins, monday to friday, ping server "scarlet" and server "magenta" and mail me if either fails to respond:

```
*/5 * * * 1-5 ( SERVER=scarlet; ping -c1 -W1 $SERVER > /dev/null 2>&1 || echo "$SERVER Not Responding To Pings, is it down?" | Mail -s "$SERVER Down" you@you.mail.com )
*/5 * * * 1-5 ( SERVER=magenta; ping -c1 -W1 $SERVER > /dev/null 2>&1 || echo "$SERVER Not Responding To Pings, is it down?" | Mail -s "$SERVER Down" you@you.mail.com )

```

But that's not a terribly great way of doing things. There's a tool called Cacti which i've used before to measure not only if a hosts up, but the latency on a network connection, the amount of disk space free on a windoze server (you just need to turn on the standard windows SNMP agent in Add/Remove programs), the amount of toner & paper left in each HP JetDirect-connected printer... etc. etc. It's very pretty and trivial to setup.

So it really boils down to which error conditions you want to catch and how much effort you want to put into it.

Hope this helps,

-c

---

### Post by EvilMarshmallow on 2007-06-14
Cacti sounds like something worth investigating.  I assume that because it can handle the printer toner & paper it can also handle checking whether a specific service is active?

Some of the things I check are:  
a fax receiving service, 
a ping to my network switches to verify that they're active, 
a URL test to verify whether certain websites are up, 
and disk space checks on a couple of servers,
along with the server pings.

How can I get a copy of Cacti to try out?

---

### Post by Wardazo on 2007-06-14
I'm coming at this problem assuming your talking about a web server.

The following site offers free website monitoring:

[http://mon.itor.us](http://mon.itor.us) 

But it only checks every 30 min. if the site id down it emails you,as well as weekly reports.

If it's for an important site then I'd always want to write my own script to check up on it, so that:

1. Checks are very frequent
2. I get a more accurate email report on the problem 

You shouldn't underestimate 2 on an important site. For example, just knowing that the problem is with your MySQL databases can save you a that little bit of time that can be the difference between a client noticing that the site is down... and not noticing;).

If you are interested in writing your own script, post on the forum exactly what you want to monitor.

---

### Post by meatpan on 2007-06-14
A great package for resource monitoring is zenoss ([www.zenoss.com](www.zenoss.com)).  The zenoss project was featured on sourceforge a while back.  

You can configure the tool to issue keep-alive requests, poll cpu-usage, inspect running process, analyze network activity, and quite a bit more.  I have been using the tool at work for about two months and so far I'm pretty impressed.

---

### Post by Railsbuntu on 2008-03-10
Hi,

I have been experiencing some very bad issues with Monit: it was unable to correctly start processes while starting them by hand worked perfectly, and when monitoring the Citadel mail server, my cpu usage would go through the roof.

I will give a try at Cacti and Mon.

---

### Post by rickyjones on 2008-03-10
I've had good luck with Nagios in the past.

-Richard

---

### Post by SpaceTeddy on 2008-03-10
i'll second the nagios opinion... we've been using that large scale on over 150 services and it performs well on a *very* old machine (P-II 200 PRO, 96 mybte ram).

---

