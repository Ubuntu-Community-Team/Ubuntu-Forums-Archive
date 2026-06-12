---
title: "(CRON) error (grandchild #11934 failed with exit status 127)"
date: 2011-05-17
forum: Server Platforms
---

### Post by leesir88 on 2011-05-17
I solved this cron issue in ubuntu.

========
This cron job line will have error 127 in ubuntu server 11.04.
*  *	* * *	root    /bin/date > /var/log/date.txt

May 17 12:34:01 gw1 CRON[11934]: (root) CMD (root    /bin/date > /var/log/date.txt)
May 17 12:34:01 gw1 CRON[11932]: (CRON) error (grandchild #11934 failed with exit status 127)
May 17 12:34:01 gw1 CRON[11932]: (CRON) info (No MTA installed, discarding output)
May 17 12:34:01 gw1 CRON[11935]: (root) CMD (   /bin/date > /var/log/date.txt)

========
This cron job line will NOT have error 127 in ubuntu server 11.04.
*  *	* * *	root    cd / ; /bin/date > /var/log/date.txt

May 17 12:38:01 gw1 CRON[11961]: (root) CMD (root    cd / ; /bin/date > /var/log/date.txt)
May 17 12:38:01 gw1 CRON[11962]: (root) CMD (   cd / ; /bin/date > /var/log/date.txt)
May 17 12:38:01 gw1 CRON[11959]: (CRON) info (No MTA installed, discarding output)

========
The file in /var/log/date.txt generated successfully with this contents.
Tue May 17 12:38:01 HKT 2011

========
It seems the exit code is default to 127 and not set to the command. The added command "cd / ;" or any success command will reset it. Then the actual command can return the exit code properly. 

May be somebody should look at the cron or related source code.

========
Also, the command in the cron job line must be in full path. Such as
/bin/date
/bin/run-parts

The script files for run-parts must not have "." . Such as
gw1-dnns-sh

This will not work.
gw1-dnns.sh

======== 
I found this limitation is ubuntu server 11.04.

---

### Post by DaithiF on 2011-05-17
Hi, thanks for reporting your findings.  However the first of these is not an issue, instead you have used an incorrect format for your crontab file.

Individual users crontab files (ie. those edited via crontab -e, or sudo crontab -e for root's), **DO NOT** contain a field for the user.  (since the user is already known from the ownership of the crontab)

/etc/crontab and the files in /etc/cron.d and /etc/cron.{hourly, daily, weekly, monthly} **DO** contain a field for the user.

so your entry:```

* * * * * root /bin/date > /var/log/date.txt

``` is only valid for either /etc/crontab, or within a file in one of the cron directories.  I'm surmising however that you had that in root's crontab, ie. sudo crontab -e.

If you put that entry in a users crontab, the piece **root /bin/date > /var/log/date.txt** gets treated as the command to run, and since there is no executable on your system named root, it fails.

For your variant:
```
* * * * * root cd / ; /bin/date > /var/log/date.txt
```
**root cd / ; /bin/date > /var/log/date.txt** is the command that gets run ... the first statement (**root cd /**) will fail, but the second **/bin/date > /var/log/date.txt** will succeed, and the exit status of the last command determines the overall job success/failure as far as cron is concerned.

Regarding the second issue of file names, yes, the filename convention required for files in the /etc/cron* directories is documented in **man cron**, excerpt here:
```
Files must conform to the same naming convention as used by  run-
       parts(8):  they  must  consist solely of upper- and lower-case letters,
       digits, underscores, and hyphens.

```

---

