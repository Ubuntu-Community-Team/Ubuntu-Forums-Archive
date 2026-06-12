---
title: "Syslog file permission"
date: 2011-10-10
forum: Server Platforms
---

### Post by lrinetti on 2011-10-10
When i define a new log file in /etc/syslog.conf what can i do so that the new file is generated with a specific permissione (i.e. 644) ? I'm using Ubuntu Server 11.04.

Thank You 
Regards

---

### Post by Jonathan L on 2011-10-10
> **lrinetti said:**
> When i define a new log file in /etc/syslog.conf what can i do so that the new file is generated with a specific permissione (i.e. 644) ? I'm using Ubuntu Server 11.04.

Thank You 
Regards

Hi Irinetti

I believe you're looking for the appropriate entries for /etc/rsyslog.conf (or /etc/rsyslog.d/*.conf), which is [COLOR=Red]$filecreatemode[/COLOR] which sets the mode for the subsequent log files. (You also might need to set [COLOR=Red]$umask[/COLOR] to get what you want).

[LIST]
[*][http://www.rsyslog.com/doc/rsconf1_filecreatemode.html](http://www.rsyslog.com/doc/rsconf1_filecreatemode.html)
[*][http://www.rsyslog.com/doc/rsconf1_umask.html](http://www.rsyslog.com/doc/rsconf1_umask.html)
[/LIST]
   
Hope that helps

Jonathan

---

### Post by lrinetti on 2011-10-10
Thank You
the examples help me solve the problem.

luciano

---

