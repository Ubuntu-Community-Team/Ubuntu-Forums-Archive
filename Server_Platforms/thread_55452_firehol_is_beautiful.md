---
title: "firehol is beautiful"
date: 2005-08-09
forum: Server Platforms
---

### Post by jfdill_2 on 2005-08-09
I finally have a firewall configuration that I am pretty happy with.  The #1 key to not hate firehol is to use the ULOG interface, that way it doesn't drown the messages and syslog files, and it is very simple to do.

First, you'll need to apt-get install ulogd.  Then, add the following line to /etc/firehol/firehol.conf, I put it near the top of the file but I don't think it matters:

FIREHOL_LOG_MODE="ULOG"

Then restart firehol.  From now on, packets should be logged to /var/log/ulog/syslogemu.log instead.

Next, I recommend to apt-get install fwanalog to get nice daily statistics reports for firehol.  You will need to make a couple changes to /etc/fwanalog/fwanalog.opts around line 38 to look at the ULOG log file instead:
```
diff -r1.1 fwanalog.opts
38,39c38,39
< inputfiles_mask="messages*"   # The name of your logfiles, with a wildcard if you want
< inputfiles_dir="/var/log"     # The directory where your logfiles are in,
---
> inputfiles_mask="syslogemu.log*"      # The name of your logfiles, with a wildcard if you want
> inputfiles_dir="/var/log/ulog"        # The directory where your logfiles are in,
```
If you chose fwanalog to run as a daily cron job, you should get e-mail reports with firehol activity.  You can also point a browser to the /var/log/fwanalog directory to view the activity in more detail with pie charts.

---

### Post by stevotower on 2008-04-01
I gave this suggestion a try and ran into a problem.  In the time since the howto was written the gnu gzip folks apparently broke zgrep, which is used extensively by fwanalog, by removing the -h option.  As a result, when fwanalog mangles the ulog output, the filenames in the zegrep results are not removed from the front of the lines.  You get output like:
[INDENT]Block statistics of your firewall, created by fwanalog 0.6.9
============================================================

----------------------------------------------------------------------------

General Summary
---------------
Blocked packets: 0
Corrupt logfile lines: 35,619
----------------------------------------------------------------------------

This analysis was produced by analog 6.0.[/INDENT]

Until they fix zgrep back to how it used to be, workaround the problem by modifying /bin/zgrep:

@@ -107,6 +107,8 @@
     files_without_matches=1;;
   (--no-f*)
     no_filename=1;;
+  (-h)
+    no_filename=1;;
   (-V | --v | --ve | --ver | --vers | --versi | --versio | --version)
     echo "$version" || exit 2
     exit;;


I submitted the problem to [email]bug-gzip@gnu.org[/email].  We'll see if anything happens.

Regards,
Steve

---

