---
title: "netboot netra x1 mirror failure"
date: 2007-02-11
forum: Sun Sparc Users
---

### Post by pwohlers on 2007-02-11
Hello-

In trying to rebuild a scrapped netra x1 with ubuntu 6.10, i've managed to figure out getting the whole netboot process working, however, the installer seems to fail in a number of places, some not such a big deal, but the last one seems kind of fatal. Hopefully someone can point out to me that this is merely 'Pilot Error' and not some sort of bug.

the things I'm finding:
1) installer, in configuring the network doesn't seem to get an address from the dhcp server (and relevant dns/gateway configs). annoying, but not a big issue.

2) The mirror selection process (as someone else had mentioned) fails. He seems to have worked around it, but the setting of the nameserver to the same as the default gateway seemed non-sensical, and didn't work. So, it's pointing to my functioning nameserver.

The error you get after you've gone past the web-proxy selection screen is:

Bad archive mirror                           
The specified Ubuntu archive mirror is either not available, or does
not have a valid Release file on it. Please try a different mirror. 

Selecting other mirrors doesn't seem to change the behavior.

Dropping to a shell, I also tried to add an /etc/hosts entry for the us.archive.ubuntu.com (and archive.ubuntu.com) mirror, but that didn't seem to work either.

From /var/log/syslog I see the following:
Feb 12 02:48:41 main-menu[1727]: (process:5334): wget: archive.ubuntu.com: Hostname lookup failure
Feb 12 02:48:41 main-menu[1727]: (process:5334): wget: us.archive.ubuntu.com: Host name lookup failure
Feb 12 02:48:41 main-menu[1727]: (process:5334): wget: us.archive.ubuntu.com: Host name lookup failure
Feb 12 02:48:41 main-menu[1727]: INFO: Menu item 'choose-mirror' succeeded but requested to be left unconfigured.
Feb 12 02:48:41 main-menu[1727]: INFO: Modifying debconf priority limit from 'high' to 'medium'
Feb 12 02:48:41 debconf: Setting debconf/priority to medium
Feb 12 02:48:41 main-menu[1727]: DEBUG: resolver (libc6): package doesn't exist(ignored)
Feb 12 02:48:41 main-menu[1727]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Feb 12 02:48:41 main-menu[1727]: INFO: Falling back to the package description for console-setup-udeb
Feb 12 02:48:50 main-menu[1727]: INFO: Falling back to the package description for console-setup-udeb
Feb 12 02:48:50 main-menu[1727]: INFO: Restoring default debconf priority 'high'
Feb 12 02:48:50 debconf: Setting debconf/priority to high
Feb 12 02:48:50 main-menu[1727]: INFO: Menu item 'di-utils-shell' selected

Is this the only way for me to install this?

Is there a way for me to try netbooting something from the cd image instead? Or try mounting another hosts' filesystem and running the cdinstaller?

Just grasping :)

Any help gratefully appreciated.

Thanks,
Peter

---

### Post by pwohlers on 2007-02-13
More info:

It didn't occur to me since it netbooted fine that there would be anything wrong with the ethernet interface.

Looking more at the logs it appears that this might be some problem with the ethernet driver.

Feb 13 04:00:21 kernel: [   14.009632] 0000:00:05.0: tulip_stop_rxtx() failed (C
SR5 0xfc540400 CSR6 0x20e0000)
Feb 13 04:00:29 kernel: [    4.828084] NETDEV WATCHDOG: eth0: transmit timed out

Anyone know why the network driver should be crapping out? It doesn't seem to be a physical or network issue on the equipment side.



Thoughts?

---

### Post by ubuntu.daemon on 2007-02-22
ya i am gettin the same errors on my x31 thinkpad, im gonna try dapper and see where that gets me.  As for the dhcp, on ur router you might have to disable its dhcp server, not the automatic that gives one out, just the server.  I can help ya out with that part, but ill let you know tomr where the 6.06 gets me.

---

### Post by ubuntu.daemon on 2007-02-22
same exact thing..... dammit.:confused:

---

