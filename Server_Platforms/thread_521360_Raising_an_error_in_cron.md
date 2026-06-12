---
title: "Raising an error in cron"
date: 2007-08-09
forum: Server Platforms
---

### Post by sphim on 2007-08-09
I wrote a python script that I want cron to run every week. I know that it is possible for cron to send an email if there is an error in running the cron job. I am wondering how you would raise an error in the python script (or in any script). Do you just use a print statement, or is there a specific log file that cron checks for errors? Is there a special python exception to raise? Thanks in advance for your help.

---

### Post by kidders on 2007-08-10
Hi there,

Normally, cron blindly mails the output of a job to the appropriate user (see cron's man page). Consequently, most cron jobs are arranged in such a way as to produce no output in the event of an error-free execution, often by redirecting debug or informational messages to /dev/null, so users only get notified when something goes wrong.

Out of convention, script writers tend to do the following, whether they are writing for cron or not ...[LIST]
[*]Diagnostic output & informational messages are piped to stdout.
[*]Errors & warnings are piped to stderr.
[*]Further attention is attracted to fatal errors using non-zero exit codes.[/LIST]If you adhere to these norms in your python scripts, you should easily be able to make cron behave the way you'd like it to, without feeling like you have to do something special.

So, for the sake of argument, imagine you made a cron job out of this...```
/usr/local/sbin/task1 >> /var/log/task1.log && /usr/local/sbin/task2 > /dev/null || /usr/local/sbin/task3
```If you conform to the three basic conventions I mentioned, cron would...[LIST]
[*]Perform "task1", hiding diagnostic output away in a log file, but retaining any error messages, so they can be mailed to the job's owner.
[*]Execute "task2", even if an error occurs ... provided it wasn't fatal (ie something that might prevent the second task from working correctly). Diagnostic messages from the second task are simply discarded.
[*]Invoke "task3" (instead of "task2") in the event of a fatal error in "task1" ... presumably to clean up any mess.[/LIST]I hope that helps.

---

### Post by sphim on 2007-08-10
Thank you for the help- that's exactly what I wanted to know. Thanks

---

### Post by kidders on 2007-08-10
No problem. :-)

Sorry for the lack of python-specific detail ... I'm still stuck in the dark ages, when it comes to scripting languages!

---

