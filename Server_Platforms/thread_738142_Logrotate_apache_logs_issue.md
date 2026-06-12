---
title: "Logrotate apache logs issue"
date: 2008-03-28
forum: Server Platforms
---

### Post by girasquid on 2008-03-28
Hello, all.

I currently have a box configured with Apache 2, AWStats, and logrotate - along with a cronjob to rotate my logs every day at 3:30 AM.

I have created virtualhosts for each of the websites running off of the system, and all virtualhost accounts are full user accounts, with everything stored under their home directory. The current folder structure for any virtualhost user is:
```

/home/user/logs
/home/user/public_html

```

[i]/home/user/logs[i] is where the log files for that specific virtualhost is stored, and I have set up AWStats configurations so that the users can view their stats. However, I am having a problem with logrotate and Apache's access.log. It appears that every time after logrotate runs, the access.log has a filesize of 0 and is no longer being written to. This is my logrotate rule:
```

/home/*/logs/*.log {
create
notifempty
daily
rotate 7
compress
sharedscripts
prerotate
/usr/share/utils/updatestats.pl
endscript
postrotate
/etc/init.d/apache2 reload
endscript
}

```

The Perl script being called in prerotate is as follows:
```

#!/usr/bin/perl -w

use strict;

opendir(SITES,"/etc/apache2/sites-enabled");
while(defined(my $site = readdir(SITES))) {
	next if $site =~ /^\.\.?$/;
	system("/usr/lib/cgi-bin/awstats.pl -update -config=$site");
}
closedir(SITES);

```

I know for certain that AWStats is being run, because I can access each virtualhost's statistics and see the changes. The crontab that runs logrotate is accessed using **sudo crontab -e**, and looks like this:
```

30 3 * * * /usr/sbin/logrotate -s /home/root/logrotate.status /etc/logrotate.conf

```

After this occurs, I find that if I connect via SSH and issue a call to **/etc/init.d/apache2 reload**, logging resumes just fine. This is what the contents of the logs directory look like:
```

root@Max:~$ ls -l /home/foo/logs/
total 104
-rw-r--r-- 1 root      root     26180 2008-03-28 08:51 access.log
-rw-r--r-- 1 root      root     11258 2008-03-28 03:24 access.log.1.gz
-rw-r--r-- 1 root      root     13527 2008-03-27 03:28 access.log.2.gz
-rw-r--r-- 1 root      root      1200 2008-03-26 07:47 access.log.3.gz
-rw-r--r-- 1 root      root      1086 2008-03-26 07:46 access.log.4.gz
-rw-r--r-- 1 foo www-data  1681 2008-03-26 07:42 access.log.5.gz
-rw-r--r-- 1 foo www-data  1157 2008-03-26 07:39 access.log.6.gz
-rw-r--r-- 1 foo www-data  4294 2008-03-26 03:29 access.log.7.gz
-rw-r--r-- 1 root      root         0 2008-03-28 03:30 error.log
-rw-r--r-- 1 root      root      2198 2008-03-28 01:52 error.log.1.gz
-rw-r--r-- 1 root      root      1669 2008-03-27 02:22 error.log.2.gz
-rw-r--r-- 1 foo www-data 15597 2008-03-26 07:05 error.log.3.gz

```
And this is what the contents of the user's home directory looks like:
```

root@Max:~$ ls -l /home/foo/
total 8
drwxr-xr-x  2 foo www-data 4096 2008-03-28 03:30 logs
drwxr-xr-x 11 foo www-data 4096 2008-03-17 10:51 public_html

```

I turned on logging for cron, and this is what the relevant areas of the log look like:
```

Mar 28 03:30:01 Max /USR/SBIN/CRON[9554]: (root) CMD (/usr/sbin/logrotate -s /home/root/logrotate.status /etc/logrotate.conf)
Mar 28 03:40:01 Max /USR/SBIN/CRON[9585]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 03:50:01 Max /USR/SBIN/CRON[9588]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:00:01 Max /USR/SBIN/CRON[9591]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:10:01 Max /USR/SBIN/CRON[9606]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:20:01 Max /USR/SBIN/CRON[9611]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:30:01 Max /USR/SBIN/CRON[9613]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:40:01 Max /USR/SBIN/CRON[9624]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 04:50:01 Max /USR/SBIN/CRON[9627]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:00:01 Max /USR/SBIN/CRON[9630]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:10:01 Max /USR/SBIN/CRON[9641]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:20:01 Max /USR/SBIN/CRON[9646]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:30:01 Max /USR/SBIN/CRON[9648]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:40:01 Max /USR/SBIN/CRON[9659]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 05:50:01 Max /USR/SBIN/CRON[9662]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:00:01 Max /USR/SBIN/CRON[9664]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:10:01 Max /USR/SBIN/CRON[9675]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:20:01 Max /USR/SBIN/CRON[9680]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:30:01 Max /USR/SBIN/CRON[9844]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:40:01 Max /USR/SBIN/CRON[9855]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 06:50:01 Max /USR/SBIN/CRON[9858]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:00:01 Max /USR/SBIN/CRON[9863]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:10:01 Max /USR/SBIN/CRON[9874]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:20:01 Max /USR/SBIN/CRON[9879]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:30:01 Max /USR/SBIN/CRON[9882]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:40:01 Max /USR/SBIN/CRON[9893]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 07:50:01 Max /USR/SBIN/CRON[9923]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:00:01 Max /USR/SBIN/CRON[9939]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:10:01 Max /USR/SBIN/CRON[9950]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:20:01 Max /USR/SBIN/CRON[9955]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:30:01 Max /USR/SBIN/CRON[9957]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:40:01 Max /USR/SBIN/CRON[9968]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)
Mar 28 08:50:01 Max /USR/SBIN/CRON[9971]: (www-data) CMD ([ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null)

```

Does anyone know what I might have configured wrong, that is making Apache stop writing to the log files? My FTP logfiles, which are also being rotated, are not having any problems being written to after a rotate.

**Edit:** I've noticed that all of the rotated files are owned by root/root - could it be that Apache needs them to be owned by someone else? If so, how would I configure that?

Thanks,
Girasquid

---

### Post by MJN on 2008-03-28
As you can manually reload Apache and restart the logging (I'm curious why you reload as opposed to restart but anyway, if it's working..) then it sounds like the reload in the postrotate section is not being called.

Try temporarily commenting out your Awstats call in prerotate and seeing how you go - perhaps the calling of that script is preventing logrotate continuing on to the postrotate section (although it is still rotating the logs so perhaps this is barking up the wrong tree).

Mathew

---

### Post by girasquid on 2008-03-28
I was told that restarting Apache would kill all connections, whereas reloading would simply reload/re-read configuration files and restart logging - without severing current connections.

---

### Post by MJN on 2008-03-28
It does, however the default used to be 'restart' as in some circumstances 'reload' could cause Apache to fall over and fail to come back up again. I'm still on 6.06 so I don't know how more recent packages are configured.

However, it's a moot point given that your manual 'reload' works as you require, so I still suggest trying to ascertain why it appears that your postrotate doesn't get actioned (it might well do but you need to find out for certain - try commenting out the awstats stuff for starters).

Mathew

---

### Post by girasquid on 2008-03-29
After commenting out my call to my awstats script, the rotate seems to have worked just fine - but, as could be expected, my AWStats has not updated. What could the script be doing that's stopping Apache from being able to write to the log files afterwards without a restart?

---

### Post by MJN on 2008-03-29
What happens if you call the Perl script manually? Does it return okay? Does logging continue?

Mathew

---

### Post by girasquid on 2008-03-29
Running the script via *perl /usr/share/utils/updatestats.pl* throws a lot of "Permission Denied" errors. Running it with *sudo perl /usr/share/utils/updatestats.pl* updates all of my stats, **and** Apache is still able to log just fine(without restarting).

---

### Post by girasquid on 2008-03-31
After a few more days of just leaving the logrotate and cronjobs to run, everything is still working fine - so it must be either awstats or my script. Do you know anything about awstats? Does it perhaps need to be run under a certain set of permissions?

---

### Post by MJN on 2008-03-31
Awstats needs to be run as root, or at least with sufficient permissions to run its own files, write to its own databases, and read Apache's log files.

Cron executes jobs as root by default so no problem there.

Mathew

---

### Post by girasquid on 2008-03-31
Alright. In that case then, is it safe to assume that it must be awstats causing the problem? This is what one awstats config file looks like:
```

LogFile="/home/foo/logs/access.log"
LogFormat=1
DirData="/var/cache/awstats/"
DirCGI="/usr/share/awstats"
DirIcons="/awstats-icons/"
SiteDomain="foo.com"
HostAliases="www.foo.com"
AllowToUpdateStatsFromBrowser=1
AllowFullYearView=3
DNSLookup=0
LoadPlugin="geoipfree"

```

---

### Post by MJN on 2008-03-31
It could be Awstats, or perhaps the way you're calling it.

Try a simple [FONT=Courier New]/usr/lib/cgi-bin/awstats.pl -config=your_config_file -update[/FONT] in the prerotate section rather than calling your iterative Perl script.

Mathew

---

### Post by girasquid on 2008-04-01
Okay - I made the change, and while awstats updated and my logs rotated, access.log still has a size of 0 - and isn't being written to. After running **/etc/init.d/apache2 reload**, the files are being written to once again. What could awstats be doing that is breaking this?

---

### Post by girasquid on 2008-04-03
After a few days of keeping an eye on it, it looks like the issue still exists - even after changing the prerotate section of my logrotate rules to just call awstats, my access.log has a size of 0. Could it be possible that logrotate is failing at some point before it manages to call **/etc/init.d/apache2 reload**?

---

### Post by MJN on 2008-04-03
Try adding something else to postrotate, e.g. **touch /tmp/logrotatetest**, then you'll know if it's getting that far.

Mathew

---

### Post by girasquid on 2008-04-04
Well, I added a **touch** line, and today the file that should exist after logrotate runs *is* there - but my logs are still untouched(the touch line was just before the Apache reload). I've shifted the order of the two commands, so now we'll see if it's failing on the Apache reload.

---

### Post by girasquid on 2008-04-07
After keeping an eye on it for a while, the file that is supposed to be created has been - **and**, mysteriously, my logfiles are accessible and I don't need to restart Apache anymore. Adding the **touch** line after the Apache reload command fixed the issue - but why?

---

### Post by MJN on 2008-04-07
Dunno - it wasn't meant to!

If you now remove the touch line does it fail? If not, treat is as coincidence.

Mathew

---

### Post by girasquid on 2008-04-09
I removed the touch line, and re-added my Perl line. This is what my logrotate config file now looks like: 
```

/home/*/logs/*.log {
create
notifempty
daily
rotate 7
compress
sharedscripts
prerotate
/usr/share/utils/updatestats.pl
#/usr/lib/cgi-bin/awstats.pl -update -config=foo.com
#/usr/lib/cgi-bin/awstats.pl -update -config=bar.com
#/usr/lib/cgi-bin/awstats.pl -update -config=baz.com
endscript
postrotate
/etc/init.d/apache2 reload
endscript
}
```

And, as of this morning, it was working - but when I compare it to the previous logrotate config file, they're virtually the same - what could have changed that made it break/unbreak?

---

### Post by girasquid on 2008-04-10
And now **this** morning, it's not working. It almost seems like it works every **second** day - but what could be changing that would only break it half the time?

---

