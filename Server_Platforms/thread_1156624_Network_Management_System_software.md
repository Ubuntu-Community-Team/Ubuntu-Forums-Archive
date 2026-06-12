---
title: "Network Management System software"
date: 2009-05-11
forum: Server Platforms
---

### Post by samosamo on 2009-05-11
I'm in search of an free/open source NMS system to graph data as well as monitor services.  I'm just *quickly* reviewing the popular products and none of these are floating my boat.  I don't want it to sound like I have A.D.D. but if I can't figure out how to do something as easy as add a host and monitor it within the first few minutes of installing, I give up and move on to the next thing.  Why shouldn't I?


Cacti: Installed from apt.  Only took a few minutes to figure out.  Displays very nice graphs from SNMP data.  No plugin library, you have to search the forums for user submitted plugins.  Does not monitor services.  For what it is, it is a pretty cool tool.

Nagios: Installed from apt.  Is this a joke?  Why is this so recommended?  I installed it but did not attempt to use it.  I'm not willing to use any web based tool that requires you to ssh into the server and edit files to configure.  I may revisit this after reading about some web-based config tools.

Zenoss Core: The free version. Installed from deb. Looks and feels like an enterprise app.  Couldn't figure it out at all. I didn't even get as far as adding a single host to monitor.

Zabbix: Installed from apt.  This one looked promising but was way too difficult to use. Couldn't figure it out at all. I didn't even get as far as adding a single host to monitor.

Anyone have any others to recommend?

---

### Post by wirelessmonkey on 2009-05-11
Network Management is not simple. There is a magnificent amount of data that can be had, and a multitude of ways to filter it, and display it. 

For your particular tastes, I **think** you might like groundworkopensource, but you won't be able to run it in jaunty without a lot of work.

---

### Post by samosamo on 2009-05-12
Well, anything can be complicated.  I don't think it should be hard to simply add a host and see if it replies to ICMP ping or an SNMP query.  I will definitely look into GroundWork and post back here.

---

### Post by wirelessmonkey on 2009-05-12
IMHO, cacti does exactly that. Easy to setup, add host, and get ICMP and SNMP data. But you want more than that, and don't want to deal with 3rd party plugins to monitor services, so you'll need to learn to use a better tool, which will be more complex. You may want to look into munin and monit as well.

Best of Luck

---

### Post by samosamo on 2009-05-15
Amazing.  GroundWork is amazing. You were dead on. I installed it using the installer downloaded from their website with the "unattended" mode.  I logged right in and added a subnet to auto-discovery, and the servers were being monitored in 5 minutes.  Didn't even have to read one document.  From here I will read documentation and spend time tweaking it to my liking but this is what I really needed to get started.  It is great that it is like a GUI for Nagios and other open source tools.  There is a great community behind it and development seems very active.  Not sure how I missed it.

---

