---
title: "Cacti Upgrade Error: Cannot modify header information"
date: 2008-10-31
forum: Server Platforms
---

### Post by limaunion on 2008-10-31
Hi, after upgrading my Ubuntu Server edition from 6.06 to 8.04 (with cacti release 0.8.7b-2ubuntu1) i'm getting the following errors:

Warning: Cannot modify header information - headers already sent by (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 121

Warning: Cannot modify header information - headers already sent by (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 122

Warning: Cannot modify header information - headers already sent by (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 123

Warning: Cannot modify header information - headers already sent by (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 124

Warning: Cannot modify header information - headers already sent by (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 125

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /etc/cacti/debian.php:30) in /usr/share/cacti/site/include/global.php on line 129

Any ideas what's going on ?
Thanks in advance!
J.

---

