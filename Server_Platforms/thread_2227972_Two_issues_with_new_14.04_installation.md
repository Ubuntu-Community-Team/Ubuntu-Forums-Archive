---
title: "Two issues with new 14.04 installation"
date: 2014-06-05
forum: Server Platforms
---

### Post by MakOwner on 2014-06-05
I had 12.04.4 running on a Dell server.  I obtained the 14.04 LTS release, and used the iso to wipe and install 14.04 fresh.

I'm seeing two issues; one is that the boot process pauses wth a message - " diskfilter writes not allowed... "  And after installing transmission-daemon, there is no way to stop the daemon.

both /etc/init.d/transmission-daemon stop and service stop tranmission-daemon fail to sop the service so that the configuraiton file can be adjusted.


Anyone have any clues about either of these?

Bueller?  Bueller?  Bueller?

---

### Post by Ian_Worrall on 2014-06-24
Your syntax is wrong. Try "sudo service transmission-daemon stop"

---

