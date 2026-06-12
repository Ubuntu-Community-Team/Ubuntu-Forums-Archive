---
title: "403 error when accessing approx repository"
date: 2006-12-25
forum: Repositories &amp; Backports
---

### Post by cybersys on 2006-12-25
We are located in rural northeast Texas using a dialup internet service.  There are seven Ubuntu machines on our local network sharing this connection.  We are trying to conserve time by setting up a local caching package repository to avoid redundant downloads during system updates.  We recently installed the 'approx' package for this purpose.  'approx' was selected because it appeared to contain a stand-alone HTTP server and we didn't wish to install or maintain a more generic web server.  The caching package repository seems to work okay via the 'localhost' internal net, but when we attempt to access it from the 'eth0' (LAN) port we get '403 forbidden' errors returned.  Is there an inetd or xinetd setup required in order to open this port to the LAN?  If not, can anyone suggest another solution?

Thanks!
](*,)

---

