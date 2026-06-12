---
title: "Snort - Log new SSH Sessions Only"
date: 2016-12-03
forum: Security
---

### Post by sniper8752 on 2016-12-03
In snort, I would like to track ssh sessions.  I know I can generate an alert every x seconds if there is still an ssh connection taking place ([http://manual-snort-org.s3-website-us-east-1.amazonaws.com/node35.html](http://manual-snort-org.s3-website-us-east-1.amazonaws.com/node35.html)).  Is there a way, instead, to generate alerts if a new SSH session has begun though?

---

### Post by sniper8752 on 2016-12-03
Also, is there a way to report in the msg function, the IP address of the offender, instead of hardcoding the static IP?  E.g. "$srvr is attempting to telnet onto host $host."

---

