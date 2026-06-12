---
title: "Squid Proxy - Service issue"
date: 2012-01-20
forum: Server Platforms
---

### Post by italiangirl-6 on 2012-01-20
Hey there, I managed to get squid proxy to run just fine. Issue I am having is with the Service commands

service squid start - works fine
service squid stop - unknown instance?
service squid restart - unknown instance?

squid# squid -k kill
FATAL: Unable to open configuration file: /etc/squid/squid.conf: (2) No such file or directory
Squid Cache (Version 2.7.STABLE9): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.004 user + 0.004 sys
Maximum Resident Size: 8704 KB
Page faults with physical i/o: 12
Aborted

I'm very confused
gedit squid.conf seems to work too. Just simple things like this has made everything difficult. when I put the proxy to say firefox it does click over to the denied page but cant see to un deny anything. I feel it's because I can't reload squid because of teh service commands not being recognized...

---

