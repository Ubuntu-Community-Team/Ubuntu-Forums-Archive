---
title: "syslog-nq/mysql problem"
date: 2009-05-13
forum: Server Platforms
---

### Post by BoneyOne on 2009-05-13
I have been tasked with setting up a log server at work to collect data from Linux, Solaris, and Windows workstations and servers...with the occasional Cisco switches tossed in for good measure.

I have my machine running syslog-ng to mysql to php-syslog-ng.

It all seems to be working...kind of.

I am only able to get localhost information in the sql database though, not any of the other servers, workstations, or switches pointing to it. When I look in at /var/log/syslog I see information from all of the various sources so I know syslog is getting it, but for some reason only the localhost information is getting into mysql.

Any ideas?

---

