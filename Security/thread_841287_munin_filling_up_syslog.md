---
title: "munin filling up syslog"
date: 2008-06-26
forum: Security
---

### Post by jure1873 on 2008-06-26
I've got syslog-ng and munin installed and my logs have too much (useless) info to be useful but I don't know how to filter it. I get this authentication lines every five minutes and the problem is that I can miss something important because I skip too quickly trough these lines from munin.

```

authpriv-info	2008-06-26 14:20:28 	
CRON[10189]: pam_unix(cron:session): session closed for user munin
authpriv-info	2008-06-26 14:20:01 	
CRON[10189]: pam_unix(cron:session): session opened for user munin by (uid=0)
authpriv-info	2008-06-26 14:20:01 	
CRON[10191]: pam_unix(cron:session): session opened for user root by (uid=0)
cron-info	2008-06-26 14:20:01 	
/USR/SBIN/CRON[10190]: (munin) CMD (if [ -x /usr/bin/munin-cron ]; then /usr/bin/munin-cron; fi)
cron-info	2008-06-26 14:20:01 	
/USR/SBIN/CRON[10192]: (root) CMD (if [ -x /etc/munin/plugins/apt_all ]; then /etc/munin/plugins/apt_all update 7200 12 >/dev/null; elif [ -x /etc/munin/plugins/apt ]; then /etc/munin/plugins/apt update 7200 12 >/dev/null; fi)
authpriv-info	2008-06-26 14:20:01 	
CRON[10193]: pam_unix(cron:session): session opened for user www-data by (uid=0) 

```

---

### Post by HalPomeranz on 2008-06-26
I use a very old, very simple tool called logcheck (aka logsentry) for filtering "uninteresting" messages out of my logs.  The basic idea is that you create a file called logcheck.ignore which contains regular expressions that match the lines from your logs that you don't care about.  It will then email you a report with the "interesting" lines that didn't get filtered out.  Once you've done a little tuning it works quite well.

Available from [http://sourceforge.net/projects/sentrytools/](http://sourceforge.net/projects/sentrytools/)

---

