---
title: "Open syslogd to log from remote host, to different file."
date: 2006-06-05
forum: Server Platforms
---

### Post by djvishnu on 2006-06-05
The title says it, I have a router that supports logging to a remote syslog, how can i  configure my syslog to accept logging, and to put the log from 10.0.10.1 in a different file?

Thank you

---

### Post by alaman on 2006-06-05
to make sysklogd work for me, I made the below two changes - 

sudo vi /etc/init.d/sysklogd 
add "-r" to the SYSLOGD="-u syslog" line...SYSLOGD="-r -u syslog"

sudo vi /etc/syslog.conf
depending on the message level you are looking to receive, I added
local4.* /newlocation to the bottom of my syslog.conf file (this worked for Cisco devices).

You can use tcpdump to determine the facility level if not local4.

---

### Post by ff2k on 2006-06-26
I know this is an old thread but...

I was also trying a way to do this. Unforunately, plain old syslogd doesn't support what the OP was trying to accomplish. The format for syslog.conf is

<log_facility>.<log_level> </logpath/logfile>

You'll have better luck with syslog-ng. :KS

---

