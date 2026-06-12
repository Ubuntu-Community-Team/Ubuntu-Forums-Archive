---
title: "Hardy LAMP servers hanging about once a day"
date: 2008-12-19
forum: Server Platforms
---

### Post by gcornelisse on 2008-12-19
I have two HP 1U AMD64 8-way servers less than a year old.  One running apache2, and one with MySQL5.  I installed Hardy over the summer and have periodically kept them up to date. I've only used the packages through apt to install and update software on the server. 

Within the last 2 weeks, and seemingly after an update/upgrade, Apache2 and MySQL stop responding on their respective servers, randomly and not at the same time.  The two servers are connected via cross-over cable on eth1.  Both have iptables, and besides that, they're vanilla LAMP servers running only one website/domain w/ SSL between the two.

I've checked the syslog, mysql logs, and apache logs without finding anything notable. Is there anything else I should be checking or monitoring? Is anyone else having this problem?

Thanks, Gary

---

### Post by albinootje on 2008-12-19
> **gcornelisse said:**
> 
Within the last 2 weeks, and seemingly after an update/upgrade, Apache2 and MySQL stop responding on their respective servers, randomly and not at the same time.  The two servers are connected via cross-over cable on eth1.  Both have iptables, and besides that, they're vanilla LAMP servers running only one website/domain w/ SSL between the two.

Can you put the debug log level higher for those applications ?

And not really related perhaps, but i'm running an imap-server on my desktop so that i can switch from email-clients whenever i like.
If i run ntpdate after the imap-server (dovecot) has started, then the imap-server will stop working. And that is visible in the logs.

Could it be a logrotate or time issue ?

---

### Post by gcornelisse on 2008-12-19
I keep the time up to date with ntpdate every night.  

I changed the Apache logs to debug.  And, I changed the MySQL log_warnings = 2.  I guess its a waiting game now.  I'll have to see if something shows up in the logs if/when either hangs.

Thanks, Gary

---

### Post by gcornelisse on 2008-12-29
I've found more.  When apache2 hangs I've got about 240 apache2 processes hanging around doing nothing.  And, they don't clear out when I restart apache.  I have to pkill them all and then restart apache.

For now I have a script pkill-ing apache and then restarting every morning.  Obviously that's not a very good solution.

---

