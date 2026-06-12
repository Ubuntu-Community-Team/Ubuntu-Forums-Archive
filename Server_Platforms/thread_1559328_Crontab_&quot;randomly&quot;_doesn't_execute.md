---
title: "Crontab &quot;randomly&quot; doesn't execute"
date: 2010-08-23
forum: Server Platforms
---

### Post by donaldvr on 2010-08-23
Hi all,

I am running ubuntu 10.04 as a web/file server. I have set up several cron jobs in the past which until recently were executing normally.  However, a few days ago, cron jobs stopped executing after a restart.  I was able to fix the problem by deleting and reentering the cron jobs, but only until the next restart.   ps -ef lists cron.  Any ideas?

Summary:
1.) Cron was working --jobs executed without error and restarts worked fine
2.) Cron jobs stopped executing after a restart about a week ago --ps -e still lists cron
3.) Removing all cron jobs and reentering them by copying and pasting fixes until next restart
4.) Cron job syntax is known to be correct since they were executing before this problem arose. 

Thanks for the help

---

### Post by craigp84 on 2010-08-24
Hi,

What does the cron log output say? Check /etc/syslog.conf for a line like:

```

cron.*                        /var/log/cron.log

```

If this is not commented out (it's active), then have a look in that file. If it is commented out then:

```

grep cron /var/log/syslog

```

instead.

This should help point out what's wrong.

---

### Post by donaldvr on 2010-08-25
craigp84, thanks for your gracious help!

I can't even find an /etc/syslog.conf file.

I guess I'll have to make one, add the line you suggested, and then see what happens.

In the meantime I ran "grep cron /var/log/syslog".  There appears to be a bunch of entries related to cron jobs that ran on the day of the last time I restarted the machine, which was about a week ago.  After that date the only entries in the log are "BEGIN EDIT" and "END EDIT" entries, which I presume are from my running "crontab -e".  Example: 
```
Aug 25 06:56:34 fileserver crontab[16832]: (root) BEGIN EDIT (root)
Aug 25 06:56:45 fileserver crontab[16832]: (root) END EDIT (root)
```

Obviously, something is wrong b/c none of the jobs run after the computer is restarted.  Is there anything else I can check?

Summary:
1) /etc/syslog.conf doesn't exist
2) I created /etc/syslog.conf and added the suggested line
3) /var/log/syslog has no entries (errors or otherwise) related to cronjobs running since my last restart.
4) I don't know what to check next?

---

### Post by LightningCrash on 2010-08-25
> **donaldvr said:**
> Thanks for the tip but...

I can't even find an /etc/syslog.conf file!

I guess I'll have to make one, add the line you suggested, and then see what happens.

Thanks again!

It should be /etc/rsyslog.conf IIRC

This is one of the areas where Anacron is handy.

---

### Post by craigp84 on 2010-08-27
> **donaldvr said:**
> craigp84, thanks for your gracious help!
I can't even find an /etc/syslog.conf file.


Don't worry about that, it was an either / or proposition, you found where the messages were going :-)

> **donaldvr said:**
> There appears to be a bunch of entries related to cron jobs that ran on the day of the last time I restarted the machine, which was about a week ago.  After that date the only entries in the log are "BEGIN EDIT" and "END EDIT" entries, which I presume are from my running "crontab -e".  Example: 
```
Aug 25 06:56:34 fileserver crontab[16832]: (root) BEGIN EDIT (root)
Aug 25 06:56:45 fileserver crontab[16832]: (root) END EDIT (root)
```


Not good, so cron's definitely aren't being run. I doubt it's anything to do with /etc/cron.allow or /etc/cron.deny files as the behaviour there is around the crontab -e command rather than what jobs run.

I wonder if the crond daemon is running? If you run "ps -efwwwH | grep cron" do you see a cron daemon? The ps command i've given you there will also show if you have 1 badly written frequently running cron job taking up all the run slots.

crond kicks off with root priveleges but even so it might be worth listing out the permissions on your /var/spool/cron/crontabs dir & crontabs in there. No funny ACLs or anything here?

What about MAC (mandatory access controls) you're not running apparmour or selinux that might be getting in the way?

If my bum was in the seat in front of that box, first check would be is crond running then i'd probably jump straight into bouncing crond and running it via an "strace".

---

### Post by donaldvr on 2010-08-27
Thanks for the intelligent and helpful reply!

You are right that to see if crond is running.  It never is after restart.  I can start it manually and everything works fine.  However after restarting several times, I've noticed that other services like apache2 also "randomly" do not start up and have to be manually executed after a reboot.

I have to admit that I'm easily flustered by issues which seem to happen and not happen from time to time.  Any advice on what I should look for?  I really appreciate your lending of expertise.

---

