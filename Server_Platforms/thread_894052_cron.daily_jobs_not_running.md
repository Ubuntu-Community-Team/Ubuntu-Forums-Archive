---
title: "cron.daily jobs not running"
date: 2008-08-18
forum: Server Platforms
---

### Post by ScootyJ on 2008-08-18
Hi all
I am fairly new to the world of Linux and am having troubles trying to determine why the jobs in my cron.daily are not running
I am running Ubuntu 8.04
this is my crontab

more /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    /etc/cron.hourly
15 6    * * *   root    /etc/cron.daily
47 6    * * 7   root    /etc/cron.weekly
52 6    1 * *   root    /etc/cron.monthly
#

And this is from the my syslog 
Aug 19 04:17:01 pelpx02 /USR/SBIN/CRON[26425]: (root) CMD (   /etc/cron.hourly)
Aug 19 04:45:38 pelpx02 -- MARK --
Aug 19 05:00:01 pelpx02 /USR/SBIN/CRON[27115]: (root) CMD (/usr/local/squid-grap
h/squid-graph --output-dir=/var/www/squid-graph < /var/log/squid/access.log)
Aug 19 05:17:01 pelpx02 /USR/SBIN/CRON[27308]: (root) CMD (   /etc/cron.hourly)
Aug 19 05:45:38 pelpx02 -- MARK --
Aug 19 06:05:38 pelpx02 -- MARK --
Aug 19 06:15:01 pelpx02 /USR/SBIN/CRON[28607]: (root) CMD (/etc/cron.daily)
Aug 19 06:17:01 pelpx02 /USR/SBIN/CRON[28723]: (root) CMD (   /etc/cron.hourly)
Aug 19 06:45:38 pelpx02 -- MARK --
Aug 19 07:05:38 pelpx02 -- MARK --
Aug 19 07:17:01 pelpx02 /USR/SBIN/CRON[14361]: (root) CMD (   /etc/cron.hourly)
Aug 19 07:45:38 pelpx02 -- MARK --
Aug 19 08:05:38 pelpx02 -- MARK --
Aug 19 08:17:01 pelpx02 /USR/SBIN/CRON[19347]: (root) CMD (   /etc/cron.hourly)
Aug 19 08:45:38 pelpx02 -- MARK --
Aug 19 09:04:34 pelpx02 crontab[7003]: (root) LIST (root)


If I run crontab -l I can see another job here and this runs fine

Any suggestions would be most welcome

scott

---

### Post by HalPomeranz on 2008-08-19
Your /etc/crontab file seems like it's incorrect to me.  Here's the default /etc/crontab file from my 8.04 machine:

```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

You can see that all of the above entries use the "run-parts" program to execute the scripts out of the /etc/cron.* directories.  The entries in the /etc/crontab that you posted are not using run-parts, which means they're trying to "execute" a directory like /etc/cron.daily, which is non-sensical.

I'm not sure how you ended up with the /etc/crontab file in your original posting, but I recommend replacing your /etc/crontab file with the one I've posted above.

---

