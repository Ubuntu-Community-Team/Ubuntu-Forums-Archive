---
title: "Network Monitoring !"
date: 2009-01-16
forum: Security
---

### Post by krsnavan on 2009-01-16
Hi !

Looking for a Graphic-Network Monitoring Tool where i can monitor Cisco Routers, Switches etc.

I need to filter  especially SYSLOG Messages according to the message category!And need to very the history etc.

Vanna

---

### Post by Kinstonian on 2009-01-17
If you're looking for log management software, you might be interested in [Splunk](http://www.splunk.com).  The free version will let you analyze I believe up to 500MB of logs a day.  If you need to analyze more logs, you need to purchase it.

If you want to do the monitoring to make sure the network devices haven't been compromised, an IDS like [OSSEC](http://www.ossec.net) might be of use.  The next version of OSSEC is supposed to be able to login to the network device, download its configuration and then compare it with the previously downloaded config in order to report changes to you.  There is also a web based GUI for OSSEC, although I haven't tried it.

---

### Post by HermanAB on 2009-01-17
Zabbix is very nice and easy to install: [http://aeronetworks.ca/zabbix-howto.html](http://aeronetworks.ca/zabbix-howto.html)

Cheers,

Herman

---

### Post by uljanow on 2009-01-18
There is also [wireshark]("http://www.wireshark.org/").

---

### Post by pdtpatrick on 2009-01-18
No no no .. get Nagios!! we use it at my job and its very easy to setup and it sends you emails when something goes wrong or about to go wrong so you dont sit there scratching your head. Also monitors routers and then makes a report and all that graphing stuff to impress your manager or executives. Did i mention its very easy to setup. Oh and new distro releases now have it part of the source list.

sudo apt-cache search nagios -- found out what version they have compiled for you.
nagios 3.0 is the current release
sudo apt-cache show nagios -- to get a quick overview

have fun!!

---

### Post by pdtpatrick on 2009-01-18
oh and nagios is free and open source :) 

i think their website is [www.nagios.org](www.nagios.org)

---

