---
title: "Lighttpd setup triggers SSL SNMP alerts"
date: 2011-03-22
forum: Server Platforms
---

### Post by elijahmuha on 2011-03-22
We are running an LMS system that uses 5 separate servers (4 physical  and 1 virtual) to load balance using haproxy and lighttpd. The physical  servers are running Debian 4.1.2 and the virtual server is running  Ubuntu 10.04 LTS. The load balancing runs like a charm, but when I add  the VM running Ubuntu into the haproxy array I get constant SNMP alerts  stating that https/SSL is down then about 5 seconds later it is back up.   When I drop the server out of the array the alerts stop.  I test the  https connection on the particular server and it appears to work  properly and the SSL certificate also appears to be installed correctly.  This didn't always happen and it seemed to start after I recently  patched the server.  So naturally my best guess is one of the security  patches doesn't agree with the set up.

Has anyone seen anything like this? Any help or direction would be greatly appreciated. Thanks!

---

