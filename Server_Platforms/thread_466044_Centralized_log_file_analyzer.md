---
title: "Centralized log file analyzer"
date: 2007-06-06
forum: Server Platforms
---

### Post by artfakt on 2007-06-06
hi,

i'm searching for a solution to centralize all logs, analyse them to alert me in real time when necessary, and periodicaly report me summary informations.

that's a lot :)

[LIST]
[*]Centralize : syslog-ng is perfect for that
[*]Analyze : Searching for a modular logfile analizer, that could work with different logfile format : HTTP, XFER, SQUID, MAIL, iptables ... and also router, switch, firewall, loadbalancers... with the specificities of each of them (i mean cache for squid...)
=> ModLogAn seems interesting but not so active and documented
[*]Alert : maybe logcheck with a welll configured alert-database can do the trick ? but tricky
[*]Report : cf analyze + mail ?? 
[/LIST]

and this should not became a duplicate of what is done with SNMP : really important alerts (TRAP), ressources usage, graph, availability reports...

just want to launch this thread, any idea is appreciated..

PS: don't know any all-in-one solution that could already do that, do you ?

---

### Post by Mr. C. on 2007-06-06
Start with logwatch for summary reports and logcheck for alerts.  Both have strengths and weaknesses.

MrC

---

### Post by akvik on 2007-11-29
I've made a little script that is not very advanced, but it checks the logs that I want to check:
[http://ubuntuforums.org/showthread.php?t=627086](http://ubuntuforums.org/showthread.php?t=627086)

---

