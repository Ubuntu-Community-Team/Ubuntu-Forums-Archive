---
title: "[SOLVED] rsnapshot started  from cron is only doing partial work"
date: 2007-07-14
forum: Server Platforms
---

### Post by StoneDragon on 2007-07-14
Hi there

rsnapshot started from cron only does part of the backups. It leaves /var/run/rsnapshot.pid behind even though the process is not running anymore.
If I start the same script by hand, all the backups are made flawlessly. I have this problem on all my ubuntu-boxes, so I blame Cron for it.

Before you ask: I already put verbosity to 5 and checked the logs. There is absolutely no hint about a problem, it just stops without cleaning up stuff. Also changing pathes and configuration did not help and using daily or hourly does not make any difference.

Googling brought up some other guys with the same problem, but not yet a solution.

Thanks for any suggestions.

---

### Post by Mr. C. on 2007-07-15
New users who do not understand the environment under which cron operates, blame it when things work via command line, but not via cron.  You can blame cron all you want, but that won't make it guilty.

Once you understand the cron environment, you can narrow the scope of the problem.

First, cron runs with a limited PATH, and few environment variables.  It runs jobs with the appropriate UID/GID, has no directly attached terminal, and typically emails STDOUT/STDERR output.  Furthermore, many cron jobs are often specified to redirect STDOUT and STDERR to /dev/null, leaving  no debug trace when something fails.

Sometimes you have to work backwards to find the cause of the problem.  You say that .pid files are not being cleaned up.  Then, you must examine the source and determine how and when they are removed under normal operations, and work backwards to find where the script is exiting prematurely.

Have you checked the email for the user owning the crontab ?

MrC

---

### Post by StoneDragon on 2007-07-16
Hmm...I don't think, that I'm quite a "new user" :), but maybe I did not make clear, what I have already tested...but be assured, there was no STDERR / STDOUT redirection and the crontab was root, and I already tested the system's cron (/etc/crontab) etc. etc.

In the meantime already found the problem thanks to another forum pls. see [http://kubuntuforums.net/forums/index.php?topic=3085000.msg79527#msg79527](http://kubuntuforums.net/forums/index.php?topic=3085000.msg79527#msg79527) (and yes, I still blame cron for killing the process in the middle of work).

I had to install mailx and use a MAILTO variable in the crontab. Since I tested on 3 machines different setups (1  without MTA, the other with MTA), I can definitely confirm the problem. Although one can say, a system without MTA does not make sense anyway, I think cron should at least tell syslogd about it, when killing a process prematurely, but as you said, I don't know cron's source code, so I can't tell where the problem is happening.

Anyway, I consider it as solved by now.

---

### Post by Mr. C. on 2007-07-16
Again, you can blame cron all you want, but this is incorrect.  This is an typical RTFM problem:
> 
$ **man cron**
...
       command to see if it should be run in the current minute.  [B]When execut-
       ing commands, any output is mailed to the owner of the crontab  (or  to
       the  user  named  in the MAILTO environment variable in the crontab, if
       such exists).[/B]

As I said, new users (of cron) don't know this and blame cron for their lack of understanding.

These programs are not fickle - the work in a predictable, reliable fashion.  What one attributes to black magic another considers technology and science.  I prefer the latter.

MrC

---

### Post by StoneDragon on 2007-07-16
> **Mr. C. said:**
> Again, you can blame cron all you want, but this is incorrect.  This is an typical RTFM problem:


As I said, new users (of cron) don't know this and blame cron for their lack of understanding.

These programs are not fickle - the work in a predictable, reliable fashion.  What one attributes to black magic another considers technology and science.  I prefer the latter.

MrC

You're absolutely right, I will stop blaming cron now for not telling me why killing a process :)
No, seriously, maybe the distribution (i.e. the dependancies or standard configuration) is the cause. If cron relies on an installed MTA or even only the MAILTO variable, then why isn't an MTA installed by default or at least the MAILTO variable put into /etc/crontab for example?
Let's just imagine a standard user who wants to setup a backup job using rsnapshot or equal. Ok ok, never ever a standard user would do such a complicated thing *grin*

EDIT: and btw, it used to work on edgy (this is a standard sentence of many posts, I know)

---

### Post by Mr. C. on 2007-07-16
> **StoneDragon said:**
> ...for not telling me why killing a process

It *can't* tell you because a) there is no attached terminal to send output, and b) there was no mechanism to deliver notification.  It is up to the script (rsnapshot) to properly log and notify error conditions, which is does not do.

I hear your point - it is pretty silly for the distro to not require an MTA/MDA when cron is in use.  Silly indeed.

MrC

---

### Post by StoneDragon on 2007-07-16
Thanks, btw. the problem never appeared on scripts in crontab, that ran quick (like ntpdate), or at least I never noticed ...hmmm...let me think again....

With gusty gibbons beta, I might test some scripts with cron (without MTA / MAILTO), that are running a certain time (sleep 60 and above and echoing a count into a logfile for example), to check, if cron bails out at a certain point, where it wants to put stuff into a mail message.

---

### Post by Mr. C. on 2007-07-16
Please consider that once cron spawns a shell to start a job, it is entirely out of the picture aside from sending the output somewhere.  It has no control whatsoever beyond this.

It is very similar to doing this:

```
 (ls  2>&1 > /dev/null &)  

```
Try it.

MrC

---

### Post by StoneDragon on 2007-07-16
> **Mr. C. said:**
> Please consider that once cron spawns a shell to start a job, it is entirely out of the picture aside from sending the output somewhere.  It has no control whatsoever beyond this.

It is very similar to doing this:

```
 (ls  2>&1 > /dev/null &)  

```
Try it.

MrC

You are right once again. I did not remind, that cron forks & exec's a new shell (is this correct?). But this makes it even worse for me to understand why:
1.) the script started manually runs through without problems
2.) the jobs runs o.k. with an MTA / MAILTO var.

So much for the black magic, but let's not walk in the dark, as said I will test it on Gutsy, and with a little luck it's no issue anymore.

---

### Post by mlissner on 2008-07-18
Unbelievable. That seems to fix it: apt-get install mailx, choose local server.

I don't know who or what to blame, but I'm annoyed that that was the problem.

---

