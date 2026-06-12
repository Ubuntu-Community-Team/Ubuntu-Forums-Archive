---
title: "need free managed dns service preferably with cheap mail backup and Ubuntu daemon"
date: 2007-12-04
forum: Server Platforms
---

### Post by kraymore on 2007-12-04
need free managed dns service for web and mail hosting, preferably one that does mail backup for free (or cheap), and with the ability to update ip address through an ubuntu daemon.   want something free.  needs to update ip address with ubuntu daemon.

---

### Post by timcredible on 2007-12-04
not sure i understand, but there's plenty of hosters that will give you a lot of mail/web/etc. services for $6/month

---

### Post by MJN on 2007-12-04
[www.zoneedit.com]("http://www.zoneedit.com") provide free DNS and you can use the [Zoneclient](http://zoneclient.sourceforge.net/) Python script to update the zone(s).
 
Amongst other services they do provide a backup MX service (stores/forwards for upto 10 days I seem to recall) although I think they charge for this. Speaking of charging, everything is done on a credits basis (check the site out and you'll see what I mean) which takes a bit to get your head around but all-in-all it's not particularly expensive.
 
Mathew

---

### Post by kraymore on 2007-12-04
how do i add the necessary update line to a cron job in Gutsy also at what interval should it be run.  i dont know anything about cron jobs.  

thanks

---

### Post by MJN on 2007-12-05
Sorry about the delay - I put off responding and ended up completely forgetting.

Anyway, create a file (owned by root) in /etc/cron.d/ (say, /etc/cron.d/zoneclient) with the following in it (adjust <variables> as required):

```

#!/bin/sh
# Crontab to check the public IP address and update the DNS accordingly

# Any output (update or errors) mailed to ...
MAILTO=root

# min hour dayofmonth month dayofweek
# Note: If dayofmonth AND dayofweek are present then command is executed when EITHER is tru
e!

# Run zoneclient script on the hour every hour
00 * * * * root <path to script>/zoneclient.py --syslog -d <path to script> -r dynamic.zoneedit.com/checkip.html <zoneedit_username> <zoneedit_password> *.yourdomain.com,yourdomain.com
```This will check your public IP every hour and, if it has changed, update your DNS (yourdomain.com and *.yourdomain.com records) at ZoneEdit.

This periodic checking will be logged in /var/log/syslog and, if an update occurs, root will be sent a mail to that effect.

Just shout if you need further explanation.

Mathew

---

