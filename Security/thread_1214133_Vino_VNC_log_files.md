---
title: "Vino VNC log files"
date: 2009-07-15
forum: Security
---

### Post by XCan on 2009-07-15
Does anyone know where or even if Vino logs anything, and where its logfiles are? It would be quite interesting to see how often I am scanned by bots.

Oh, also, I noticed that in, for example, the Remote Desktop Viewer, there is this 'Hosts nearby' thingie, which shows bunch of "<user>'s Remote Desktops" in my network. Does anyone know how it works? I would very much like to block my VNC server from showing up.

---

### Post by bodhi.zazen on 2009-07-15
VNC is not so secure. If you must connect via VNC I highly suggest VNC over ssh.

You can also use ssh directly (ssh -X ) and forward a single application or an entire desktop.

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

The other solution is to restrict access to VNC with a firewall, ie iptables .

---

### Post by XCan on 2009-07-15
I am already tunneling through SSH whenever I do connect. However, I'm still interested in the log files, if only out of curiousity or educational purposes. 

Also, since the first thing I did was to switch the default port of the VNC server, I am very curious of how other PCs on the same network can still discover that I am running a VNC server.

---

### Post by XCan on 2009-07-20
*bump*

---

