---
title: "L2TP gui makes no attmpt to connect"
date: 2013-10-18
forum: Server Platforms
---

### Post by kevpatts2 on 2013-10-18
Using  Ubuntu 12.04. When I set up an L2TP connection and then try to connect  to it I am prompted for my passphrase. I enter it and nothing happens.  There is nothing logged in syslog and no interface is created. It seems  that there is no connection attempted.


 When It starts at boot these lines are logged:
Oct 18 11:06:14 L2tpIPsecVpnControlDaemon: Starting L2tpIPsecVpnControlDaemon
Oct 18 11:06:14 L2tpIPsecVpnControlDaemon: L2tpIPsecVpnControlDaemon started
Oct 18 11:06:32 L2tpIPsecVpn: "sni-qt/1876" WARN  11:06:32.073 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE



Can anyone help?

---

