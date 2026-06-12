---
title: "http log list"
date: 2010-08-09
forum: Security
---

### Post by yashar on 2010-08-09
hello,

i have a server for internet sharing by iptables, if i want to log http requests by users is there any other way other than proxy server and dansguardian? a simpler way?!     ;-)

---

### Post by bodhi.zazen on 2010-08-09
Define "simpler way" and how you want to review the data.

You can do this with anything from iptables to using a proxy such a squid.

See :

[http://wiki.squid-cache.org/SquidFaq/SquidLogs](http://wiki.squid-cache.org/SquidFaq/SquidLogs)

There are several log analysis tools listed on the bottom of this page :

[http://www.visolve.com/squid/Squid_tutorial.php](http://www.visolve.com/squid/Squid_tutorial.php)

I think you first need to determine what exactly you wish to log and how you wish to review the logs.

---

### Post by yashar on 2010-08-10
i want to know source ip ( my network user ip ) and requested http address, for example i want to know 192.168.10.76 visit which http addresses.

---

