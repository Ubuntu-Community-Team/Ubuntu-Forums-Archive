---
title: "crontab schedule updates 2nd Sunday at specific time"
date: 2017-10-03
forum: Server Platforms
---

### Post by ecrosby on 2017-10-03
Hopefully I am posting this in the correct area...
I've found online a crontab schedule that is supposed to run updates on the 2nd Sunday of the month but it did not work. This is under the root crontab. Here is what I have that is also supposed to generate a log:

```
[I]0 2 8-14 * * if [ `date +\%a` = Sun ]; then /root/bin/update.sh; fi > /root/update.log 2>&1
[/I]
```
The update.sh script looks like this:

```
*#!/bin/bash*
*PATH="/usr/local/sbin:/usr/sbin:/sbin:$PATH"*
*apt-get update*
*apt-get upgrade -y*
[I]apt-get autoremove -y

[/I]
```

As mentioned, this schedule did not run nor did it create the log. What did I do wrong?
Thanks in advance.

---

### Post by TheFu on 2017-10-04
Through 20+ yrs of experience, I've found that automatic patching is dangerous.  Usually, everything is fine, except when it isn't. That happens about 1 time a year and lots and lots of bad things happen.

There are built-in methods to automatically patch an Ubuntu server.  Why not use those instead?  You can run only security patches (which would be smarter) automatically too.  Google will find those answers quickly.

I put this in every crontab file - for reference:```

# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
```

$ man -s 5  crontab
has all the details about the format of the crontab files on your system, BTW.  It is worth a read to understand this stuff. Fairly simple.  I'd do something like Day of the month from 7-14 and Day of the Week is only Sunday. The "fields" of the crontab are OR fields, so if you use both, then if either 1 is true, the job is run.  That means your test for "Sun" makes sense.  

What did you do wrong?  I think you need to quote the "Sun" part.  Also, I'm not certain that the %a needs to be escaped.

Really, I'd just enable automatic security patches (daily) and do the other patching manually, weekly, with lots of logging (which is what I do there for 20-30 systems).  I like knowing exactly when a patch runs so should anything go wrong, I it fresh in my mind what changed. 
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)

---

### Post by ecrosby on 2017-10-04
> **TheFu said:**
> Through 20+ yrs of experience, I've found that automatic patching is dangerous.  Usually, everything is fine, except when it isn't. That happens about 1 time a year and lots and lots of bad things happen.

There are built-in methods to automatically patch an Ubuntu server.  Why not use those instead?  You can run only security patches (which would be smarter) automatically too.  Google will find those answers quickly.

I put this in every crontab file - for reference:```

# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed
```

$ man -s 5  crontab
has all the details about the format of the crontab files on your system, BTW.  It is worth a read to understand this stuff. Fairly simple.  I'd do something like Day of the month from 7-14 and Day of the Week is only Sunday. The "fields" of the crontab are OR fields, so if you use both, then if either 1 is true, the job is run.  That means your test for "Sun" makes sense.  

What did you do wrong?  I think you need to quote the "Sun" part.  Also, I'm not certain that the %a needs to be escaped.

Really, I'd just enable automatic security patches (daily) and do the other patching manually, weekly, with lots of logging (which is what I do there for 20-30 systems).  I like knowing exactly when a patch runs so should anything go wrong, I it fresh in my mind what changed. 
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)
[https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)

Thank you for that information.
Yeah, I'm very familiar with crontab having created schedules in the past on numerous occasions, I've just never created one for a specific day of the month to only execute on that one day and time. I'm in a delicate situation where I am doing some consulting for a Dev company that may not be willing to pay for my time to massage regular monthly updates manually; I already have security patches enabled. I've setup automatic regular updates on some Ubuntu machines at home and, so far (knock on wood), have not had any issues. Of course, there is going to be that one time and then your screwed, right? Since this web server is on AWS I have already taken measures to complete snapshots of the server before the update takes place to ensure I can roll back in case of issues. I'm sure with your 20+ years experience you have much more experience than I do, I will heed your warning and, perhaps, approach my clients to see if they would be willing to pay me for an hour a month just to complete the manual updates.
In the meantime, I'll take a look at those links and make fixes based on your suggestions and see what happens.
Thanks again.

---

### Post by LHammonds on 2017-10-06
I have also been leery about automatic upgrade due to my initial experience learning on Ubuntu Server 10.04.  But (knocks on wood) I have not had those boot up problems on 12.04, 14.04 nor 16.04 yet.  I recently got tired of doing these updates manually so I scheduled them to be fully automatic.

However, I did so in the same manner I did it manually. I let my Guinea pig server do the 1st upgrade and wait a day before letting the others do the same process.  It still is not a guarantee there will not be specific problems on other systems but I have backups for those cases and it lets me know if there is definitely going to be a problem with the upgrade by catching it 1st on a non-mission-critical server.

EDIT: I'm also a fan of logging the results of those upgrades in log files which help track down issues after an upgrade that might have broke a feature in an app (such as a removed PHP function).  However, I bet you already do log those results and were just showing those commands in a simplistic way in your post for clarity.

LHammonds

---

