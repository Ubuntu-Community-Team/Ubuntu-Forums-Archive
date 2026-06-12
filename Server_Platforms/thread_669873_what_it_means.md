---
title: "what it means?"
date: 2008-01-16
forum: Server Platforms
---

### Post by ambush_xx on 2008-01-16
> Jan 16 23:32:37 ambush-desktop gconfd (root-20249): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 16 23:32:37 ambush-desktop gconfd (root-20249): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jan 16 23:32:37 ambush-desktop gconfd (root-20249): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jan 16 23:32:37 ambush-desktop gconfd (root-20249): GConf server is not in use, shutting down.
Jan 16 23:32:37 ambush-desktop gconfd (root-20249): Exiting
Jan 16 23:59:46 ambush-desktop -- MARK --
Jan 17 00:19:47 ambush-desktop -- MARK --
Jan 17 00:39:47 ambush-desktop -- MARK --
Jan 17 00:59:47 ambush-desktop -- MARK --
Jan 17 01:19:47 ambush-desktop -- MARK --
Jan 17 01:39:48 ambush-desktop -- MARK --
Jan 17 01:59:48 ambush-desktop -- MARK --
Jan 17 02:19:48 ambush-desktop -- MARK --
Jan 17 02:39:48 ambush-desktop -- MARK --
Jan 17 02:59:49 ambush-desktop -- MARK --
Jan 17 03:19:49 ambush-desktop -- MARK --
Jan 17 03:39:49 ambush-desktop -- MARK --
Jan 17 03:59:49 ambush-desktop -- MARK --
Jan 17 04:19:50 ambush-desktop -- MARK --
Jan 17 04:39:50 ambush-desktop -- MARK --
Jan 17 04:59:50 ambush-desktop -- MARK --
Jan 17 05:19:50 ambush-desktop -- MARK --
Jan 17 05:39:51 ambush-desktop -- MARK --
Jan 17 05:59:51 ambush-desktop -- MARK --
Jan 17 06:19:51 ambush-desktop -- MARK --
Jan 17 06:39:51 ambush-desktop -- MARK --
Jan 17 06:59:52 ambush-desktop -- MARK --
Jan 17 07:19:52 ambush-desktop -- MARK --


What does this mean?? the MARKs. Its part of var/log/messages

---

### Post by r00tintheb0x on 2008-01-16
Every twenty or so mins, the syslog daemon "-- MARK --'s" the log to let you know its working.

---

### Post by ambush_xx on 2008-01-16
Ok thanks...

---

