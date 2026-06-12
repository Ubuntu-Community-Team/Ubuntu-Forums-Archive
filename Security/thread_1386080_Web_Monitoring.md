---
title: "Web Monitoring"
date: 2010-01-20
forum: Security
---

### Post by thatboysabin on 2010-01-20
I want to do some web monitoring.  I have an ubuntu server setup on an old Dell PowerEdge 700.  I setup dansguardian, squid, sarg, and apache with webmin.  The network is a windows based network.  What id like to do is just track websites that are visited and what not.  Im not really concerned with blocking anything.  I have dansguardian setup in silent mode but i havent really found a good way to view the logs.  I want the logs to be seperated by local internal IP of each user.  Right now, with people connecting to dansguardian, viewing the squid logs it only shows the 127.0.0.1 IP.  I guess this is because dansguardian forwards everything to squid so squid only shows 1 IP as coming in.  Should i just setup SQUID only?  Are there better solutions?  Real time bandwidth usuage would be nice also.  We have a cisco PIX firewall which i guess i could connect to the HUB on it and put another NIC in and have the server read all the data coming across but what software would I use to analyze all that?   Can anyone list any good tutorials or solutions to this?  Thanks.

Jared

---

### Post by bodhi.zazen on 2010-01-20
See these links :

[http://martybugs.net/smoothwall/squidlogs.cgi](http://martybugs.net/smoothwall/squidlogs.cgi)

[http://www.squid-cache.org/Scripts/](http://www.squid-cache.org/Scripts/)

---

### Post by pirateghost on 2010-01-20
if you arent looking to block anything, just use squid with sarg.  sarg will give you a day by day, ip by ip list of usage.  its really handy

---

