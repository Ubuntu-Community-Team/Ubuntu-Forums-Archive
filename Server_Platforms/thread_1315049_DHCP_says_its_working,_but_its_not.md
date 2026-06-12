---
title: "DHCP says its working, but its not"
date: 2009-11-04
forum: Server Platforms
---

### Post by fowie on 2009-11-04
Hardy Heron (yep, old school) running on my server, suddenly dhcp3-server stopped working.  I modified my syslog.conf so that the log output of dhcpd would go to /var/log/dhcpd.log, and when I restart dhcpd it says "ok", but I don't get anything in the log, not even a successfuly started message.  Also, no clients can connect to the dhcp server to get an ip address. How can I track down this problem?

--FIXED--
I uninstalled the server, deleted the apt cache .deb, and reinstalled, then it worked.

---

### Post by Iowan on 2009-11-05
[SOLVED]?
(Thread Tools)

---

