---
title: "syslog CRON errors"
date: 2012-05-17
forum: Server Platforms
---

### Post by jrtboht on 2012-05-17
I'm getting the following errors in my syslog


```
May 17 08:09:01 webserver CRON[18834]: (CRON) info (No MTA installed, discarding output)
May 17 08:10:02 webserver CRON[18847]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:10:02 webserver CRON[18848]: (www-data) CMD ([ -x /usr/share/awstats/tools/update.sh ] && /usr/share/awstats/tools/update.sh)
May 17 08:10:02 webserver CRON[18846]: (CRON) info (No MTA installed, discarding output)
May 17 08:10:02 webserver CRON[18845]: (CRON) info (No MTA installed, discarding output)
May 17 08:15:01 webserver CRON[18860]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:15:01 webserver CRON[18859]: (CRON) info (No MTA installed, discarding output)
May 17 08:17:01 webserver CRON[18863]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 17 08:20:01 webserver CRON[18869]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:20:01 webserver CRON[18870]: (www-data) CMD ([ -x /usr/share/awstats/tools/update.sh ] && /usr/share/awstats/tools/update.sh)
May 17 08:20:01 webserver CRON[18868]: (CRON) info (No MTA installed, discarding output)
May 17 08:20:01 webserver CRON[18867]: (CRON) info (No MTA installed, discarding output)
May 17 08:25:01 webserver CRON[18882]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:25:01 webserver CRON[18881]: (CRON) info (No MTA installed, discarding output)
May 17 08:30:01 webserver CRON[18886]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:30:01 webserver CRON[18887]: (www-data) CMD ([ -x /usr/share/awstats/tools/update.sh ] && /usr/share/awstats/tools/update.sh)
May 17 08:30:01 webserver CRON[18885]: (CRON) info (No MTA installed, discarding output)
May 17 08:30:02 webserver CRON[18884]: (CRON) info (No MTA installed, discarding output)
May 17 08:35:01 webserver CRON[18901]: (getmail) CMD (/usr/local/bin/run-getmail.sh > /dev/null 2>> /var/log/ispconfig/cron.log)
May 17 08:35:01 webserver CRON[18900]: (CRON) info (No MTA installed, discarding output)
```

this is a webserver that I don't use for mail.  can anyone identify what this is?  Thanks!

---

### Post by LHammonds on 2012-05-17
1st, have a look at **/usr/local/bin/run-getmail.sh** and see what it is trying to do.  I would guess it is trying to access a Message Transfer Agent (MTA) such as postfix.  The server may not be configure as a proper mail server but it might expect the ability send or get mail from a mail server.

---

### Post by jrtboht on 2012-05-17
Here is the contents of run-getmail.sh

```
#!/bin/sh
PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/local/sbin:/usr/local/bin:/usr/X11R6/bin
set -e
cd /etc/getmail
rcfiles=""
for file in *.conf ; do
if [ $file != "*.conf" ]; then
rcfiles="$rcfiles -r $file"
fi
done
#echo $rcfiles
if [ -f /tmp/.getmail_lock ]; then
  echo 'Found getmail lock file /tmp/.getmail_lock, we quit here.'
else
  touch /tmp/.getmail_lock
  if [ "$rcfiles" != "" ]; then
    /usr/bin/getmail -n -v -g /etc/getmail $rcfiles
  fi
  rm -f /tmp/.getmail_lock
```

I also tried to check /var/log/ispconfig/cron.log but I have no /var/log/ispconfig directory.  The /etc/getmail directory is empty

---

### Post by LHammonds on 2012-05-18
Does **/usr/bin/getmail** exist?

I did a quick check and getmail comes from the "getmail4" package which is not installed by default.  Someone had to install it.

And from the looks of that script, it is expecting a configuration file(s) in /etc/getmail

The [Options page]("http://pyropus.ca/software/getmail/configuration.html#running-commandline-options") shows that the commandline options as used in the script are trying to retrieve new messages.

Since you said their are no files in /etc/getmail like what the script wants to use, it may default to the ~/.getmail/getmailrc file to get its options.

But regardless, is there some function on your (web) server that requires grabbing email from a mailbox?

These errors might be related to the config file being deleted or a change in the [requirements for getmail]("http://pyropus.ca/software/getmail/documentation.html#requirements").

LHammonds

---

### Post by jrtboht on 2012-05-18
/usr/bin/getmail does exists.  I played around with installing Citadel a while back but didn't really like it and switched to using google apps for mail on my domains.  So I don't have any need for grabbing email on this server.  Would it be safe to remove getmail4 and would that solve the problem?  Better yet, is CRON a scheduler, if so there must be a way to edit CRON so that it stops checking for mail.

---

### Post by koenn on 2012-05-18
yes, cron is a task scheduler.

look in /etc/crontab and in directories that have names starting with /etc/cron

---

### Post by LHammonds on 2012-05-20
> **jrtboht said:**
> /usr/bin/getmail does exists.  I played around with installing Citadel a while back but didn't really like it and switched to using google apps for mail on my domains.  So I don't have any need for grabbing email on this server.  Would it be safe to remove getmail4 and would that solve the problem?  Better yet, is CRON a scheduler, if so there must be a way to edit CRON so that it stops checking for mail.
I wouldn't simply delete programs.  I would find out what / how it got installed and go through the correct process of uninstalling it and related files if you really do not need them on your server.

As for your crontab schedule, yes, you can keep it from running by editing the schedule and that should be the 1st thing you do.  However, I'd recommend a cautious method for doing so, especially if new to Linux.  I assume the crontab that is running that command is under the root ID...but you would need to verify that.  Here are [my notes about a crontab schedule]("http://ubuntuforums.org/showpost.php?p=11938261&postcount=14") and how I maintain my schedules (the less dangerous way than editing crontab directly)

LHammonds

---

