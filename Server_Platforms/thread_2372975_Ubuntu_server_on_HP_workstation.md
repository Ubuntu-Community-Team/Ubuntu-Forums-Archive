---
title: "Ubuntu server on HP workstation"
date: 2017-10-01
forum: Server Platforms
---

### Post by katiais on 2017-10-01
[COLOR=#070F14][FONT=Verdana]Hi, I have HP workstation Z440 : Xeon W3520 and I want to make on it Ubuntu server.
Is it compatible? 
thank you.
[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana][/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana][/FONT][/COLOR]

---

### Post by howefield on 2017-10-01
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by darkod on 2017-10-01
If you have no important data on it and you can format and install, I suggest you try it. That is the best way. Many times big brands are late with officially certifying an OS, and for Linux they mostly cover Redhat and Centos. But that doesn't mean Ubuntu Server can't be installed and run correctly on your machine. Try it and you will know...

Otherwise it might be difficult to find information for that model specifically.

---

### Post by mastablasta on 2017-10-02
well that was fast... 

[http://www8.hp.com/h20195/v2/GetPDF.aspx/c04400038.pdf](http://www8.hp.com/h20195/v2/GetPDF.aspx/c04400038.pdf)

> OverviewForm Factor Minitower
Operating Systems Preinstalled:
&#61623; Windows 10 Pro 64
&#61623; Windows 10 Pro 64 downgrade to Windows 7 Professional 64
&#61623; Windows 10 Home 64 High-end
&#61623; Windows 8.1 Pro 64-bit
&#61623; HP Installer Kit for Linux (includes drivers for 64-bit OS versions of RHEL 6.6, RHEL 7, SUSE
Linux Enterprise Desktop 11, Ubuntu 14.04)
&#61623; Red Hat® Enterprise Linux Desktop (Paper license with 1 year support; no preinstalled OS)
Supported:
&#61623; Windows 8/8.1 Enterprise 64-bit
&#61623; Windows 7 Enterprise 64-bit
&#61623; Red Hat Enterprise Linux Desktop 6, 7
&#61623; SUSE Linux Enterprise Desktop 11 SP3, 12

quick view - it seems hardware RAID is not supported under linux, but software raid is (if you need it).

---

