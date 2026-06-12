---
title: "Logwatch and SVN"
date: 2005-09-11
forum: Server Platforms
---

### Post by dcraven on 2005-09-11
Does anyone know of a tool like Logwatch that can understand and interpret Subversion entries in an Apache log file? Logwatch does exactly what I want it to do, but fills the daily email it sends me with unidentified activity pertaining to the svn logs. Either a replacement tool or a Logwatch extension that can handle SVN logs would do.

Thanks,
~djc

---

### Post by cactus on 2005-09-19
[QUOTE=dcraven]Does anyone know of a tool like Logwatch that can understand and interpret Subversion entries in an Apache log file? Logwatch does exactly what I want it to do, but fills the daily email it sends me with unidentified activity pertaining to the svn logs. Either a replacement tool or a Logwatch extension that can handle SVN logs would do.

Thanks,
~djc[/QUOTE]
 What exactly are you trying to get from the logs? If you are trying to get stats on checkins and updates, I recommend just using a post-commit hook to perform some type of data aggregation, like maybe creating an entry in a rrd database, or just sending out an email.

If you want to track information on checkouts and so forth, then I have no ideas off the top of my head...

---

