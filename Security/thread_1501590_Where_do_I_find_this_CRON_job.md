---
title: "Where do I find this CRON job?"
date: 2010-06-04
forum: Security
---

### Post by cllow2020 on 2010-06-04
where to find this CRON job ?
 
edit....
i found it at syslog, CRON schedule check for php5:-
> 
[SIZE=2]Jun 4 14:17:01 myhostname [3690]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)[/SIZE]

[SIZE=2]Jun 4 14:39:01 myhostname CRON[3847]: (root) CMD ( [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)[/SIZE]
 
 
[SIZE=2]Jun 4 15:09:01 myhostnameCRON[3958]: (root) CMD ( [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)[/SIZE]

but i still don't understand , why / what schedule it to check php5 ? how to off it ?

---

### Post by noway2 on 2010-06-04
cllow2020,  you might get better and faster responses if you post your question under its own thread rather than appending to the end of someone else's on a different topic.  When trying to follow a thread, having it jump to a different subject is confusing.

---

### Post by cariboo on 2010-06-04
Moved to it's own thread.

---

### Post by FuturePilot on 2010-06-04
/etc/cron.d/php5

---

