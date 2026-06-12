---
title: "Need PHP-Based Dashboard Product"
date: 2007-12-10
forum: The Cafe
---

### Post by SuperMike on 2007-12-10
Can anyone recommend a PHP-based dashboard product** for Ubuntu Linux** that allows me to write small gadgets to show us business intelligence information, such as number of transactions running through an application, broke out by category, etc. I've been asked to find something with fancy charts.

I think they're interested in pentaho.com, but not something requiring Java. We know PHP.

Note this is different than just charting SNMP information like one would do with Cactus or Nagios. This is about going beyond that -- letting us have gadgets we can build to show business intelligence data. For instance, how many of our customers sent in their transactions by mail, versus sent by web, etc. We track these things in database tables but don't have a handy web interface for managers to visualize it in pretty charts and see trends over time.

And we need the system such that we have roles if possible where certain managers can see certain gadgets only, while others can see much more. (There's office politics -- that's why. Some managers may not understand that it's okay to have a set of alerts on some servers at certain times of the day.)

As for programming language, we know PHP, HTML, and Javascript. We can even use server-side Javascript (a cool new thing). But we want to avoid Java at all costs because we don't have a lot of investment in that.

Another route, perhaps, is that the portal/gadget/dashboard platform lets us build gadgets with a non-programming interface, and just point at XML outputs from some job that runs somewhere. That permits me to get our Dev team to just build the output in any programming language and the Dashboard aggregates it into pretty charts.

Note -- given the right product, we would actually $$PAY$$ handsomely for this and for its tech support contract, so please consider that.

Please also note that I have a time-limit on how long I can research this.

---

### Post by mmichalik on 2008-03-07
Did you ever find a suitable PHP solution?

I'm evaluating Pentaho but, it's not exactly what I am looking for.

Please let me know.

---

### Post by SuperMike on 2008-03-07
If it's system performance you want, go with net-snmp and then install munin. It's easy to install and has an extremely easy API to build stuff with Bash or Perl or PHP or Python or whatever so that it displays inside it's treeview as a set of charts.

Granted, learning net-snmp takes a little bit of learning to get used to, but find a mentor, or ask me a question, and I can help you overcome that hurdle. I had a mentor named Alvaro from Brazil help me get used to SNMP and net-snmp, and then I learned the 'exec' parameters in /etc/snmpd/snmpd.conf can let me run Bash scripts to return data in charts, providing yet another way to get custom charts on system performance for things such as application-specific things.

However, if you install net-snmp, then follow with munin, then install munin-node, then fire up net-snmp, munin, and munin-node, then wait about 30 minutes, you can connect to [http://127.0.0.1/munin/](http://127.0.0.1/munin/) to see the charts on your system's performance.

My thanks goes out to those Munin guys -- they made system performance far easier than Nagios or anything else out there, and they made it easy to extend.

Now if it's a dashboard you want, the only thing I think I can find is Joomla, and then you use IFRAMEs to show small PHP pages, or another website's pages, inside them as "gadgets".

---

### Post by mmichalik on 2008-03-10
I set up a development LAMP stack today for another project that requires Joomla so, I will check it out when I get it all squared away.

Pentaho is still looking like a clear cut winner to me.  Short of purchasing Business Objects for our BI reporting needs.

Thanks!

---

### Post by SuperMike on 2008-03-13
I'd say, save the cash. Stick with Joomla and just use IFRAMEs for gadgets. Then, have people make little PHP pages (or use any language you like) that stick their data in the upper-left-hand corner of the page, and then suck those in via the IFRAMEs. For charts, there are packages that one can get for free, and some that one can get for a small cost, so that developers can use that API, feed it some stats, and make gadgets.

---

### Post by dashboards on 2008-05-30
Try this [Dashboard Tool]("http://www.infocaptor.com")

You can code your dashboard in plain SQL and then publish them on the server.

---

