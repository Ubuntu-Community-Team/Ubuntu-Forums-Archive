---
title: "Cron - @reboot jobs not working"
date: 2010-07-13
forum: Server Platforms
---

### Post by ceallred on 2010-07-13
Still a Ubuntu newbie but usually am able to figure things out.  This one has stumped me though.....

Have a headless server running Lucid 64 bit.  Everything is working great except for a couple of Cron jos I'm trying to have run at boot.

My user crontab looks like this:
[INDENT]# m h  dom mon dow   command
01 * * * * /home/ceallred/Scripts/SambaBkup.sh
@reboot /usr/bin/SpiderOak --headless &[/INDENT]

The SambaBkup script works like clockwork...  The SpiderOak job doesn't start.  It works if I type the command in manually.

syslog only shows:
[INDENT]Jul 13 22:45:33 RavenWing cron[1010]: (CRON) INFO (pidfile fd = 3)
Jul 13 22:45:33 RavenWing cron[1022]: (CRON) STARTUP (fork ok)
Jul 13 22:45:33 RavenWing cron[1022]: (CRON) INFO (Running @reboot jobs)
Jul 13 22:45:33 RavenWing CRON[1048]: (ceallred) CMD (/usr/bin/SpiderOak --headless &)[/INDENT]

Yet ps -A doesn't show a running SpiderOak process.  It shows after starting manually. 

Any help would be much appreciated.

---

### Post by Sanjeevtrip on 2010-07-14
[COLOR="Blue"]# m h dom mon dow command
01 * * * * /home/ceallred/Scripts/SambaBkup.sh
[/COLOR]

your cronentry says, run the script every hour first minute, so its
01:01 - 1am 1min , then
02:01 - 2am 1min , then
03:01 - 3am 1min 

how you want it to run, do you want it to run every min or once at boot.

---

### Post by DaithiF on 2010-07-14
Hi,
Is the job starting up & then erroring/exiting, or is it not being run at all?  To find out try capturing output from the job in a logfile:
e.g. /usr/bin/SpiderOak.sh --headless > /path/to/logfile 2>&1 &

reboot & see what turns up in the logfile.

---

### Post by ceallred on 2010-07-14
> **DaithiF said:**
> Hi,
Is the job starting up & then erroring/exiting, or is it not being run at all?  To find out try capturing output from the job in a logfile:
e.g. /usr/bin/SpiderOak.sh --headless > /path/to/logfile 2>&1 &

reboot & see what turns up in the logfile.

Changed crontab to this:
[INDENT]# m h  dom mon dow   command
01 * * * * /home/ceallred/Scripts/SambaBkup.sh
@reboot /usr/bin/SpiderOak --headless > /home/ceallred/Scripts/SpiderOak.log 2>&1 &[/INDENT]

Still no luck.... and no SpiderOak.log file was generated.

@sanjeevtrip.... no problems with the SambaBkup job.  It's working as I like.

---

### Post by DaithiF on 2010-07-15
Hi,
Its still unclear whether the job is being launched & failing without any output (spideroak problem), or not being launched at all (cron problem).  My next suggestion to help narro down which would be to have the cron job run a wrapper script which DOES produce output (as well as launching spideroak), and again redirect the output to a log file.  something like run_spideroak.sh
```
echo "$(date) About to run spideroak"
/usr/bin/SpiderOak --headless &
echo "$(date) SpiderOak launched..., process list is $(ps -ef | grep -i spideroak)"

```
put it in your scripts directory, make it executable, and call it from cron:
```
@reboot /home/ceallred/Scripts/run_spideroak.sh > /home/ceallred/Scripts/spideroak.log 2>&1

```

---

### Post by ceallred on 2010-07-15
> **DaithiF said:**
> Hi,
Its still unclear whether the job is being launched & failing without any output (spideroak problem), or not being launched at all (cron problem). My next suggestion to help narro down which would be to have the cron job run a wrapper script which DOES produce output (as well as launching spideroak), and again redirect the output to a log file. something like run_spideroak.sh
```
echo "$(date) About to run spideroak"
/usr/bin/SpiderOak --headless &
echo "$(date) SpiderOak launched..., process list is $(ps -ef | grep -i spideroak)"

```
put it in your scripts directory, make it executable, and call it from cron:
```
@reboot /home/ceallred/Scripts/run_spideroak.sh > /home/ceallred/Scripts/spideroak.log 2>&1

```
 
 
Will try this when I get home from work tonight....   Will post results

---

### Post by ceallred on 2010-07-15
> **DaithiF said:**
> Hi,
Its still unclear whether the job is being launched & failing without any output (spideroak problem), or not being launched at all (cron problem).  My next suggestion to help narro down which would be to have the cron job run a wrapper script which DOES produce output (as well as launching spideroak), and again redirect the output to a log file.  something like run_spideroak.sh
```
echo "$(date) About to run spideroak"
/usr/bin/SpiderOak --headless &
echo "$(date) SpiderOak launched..., process list is $(ps -ef | grep -i spideroak)"

```
put it in your scripts directory, make it executable, and call it from cron:
```
@reboot /home/ceallred/Scripts/run_spideroak.sh > /home/ceallred/Scripts/spideroak.log 2>&1

```

This is killing me...  Tried the wrapper script.   Running manually generates the log file...  rebooting and the job doesn't run or create log file.

Syslog shows that CRON ran the job... but again, no output and the process isn't running.
[INDENT]Jul 15 20:07:45 RavenWing cron[1026]: (CRON) INFO (Running @reboot jobs)
Jul 15 20:07:45 RavenWing CRON[1053]: (ceallred) CMD (/home/ceallred/Scripts/run_spideroak.sh > /home/ceallred/Scripts/SpiderOak.log 2>&1 &)[/INDENT]

It's seems like cron doesn't like the @reboot command....  Any other ideas?

---

### Post by ceallred on 2010-07-16
> **ceallred said:**
> This is killing me...  Tried the wrapper script.   Running manually generates the log file...  rebooting and the job doesn't run or create log file.

Syslog shows that CRON ran the job... but again, no output and the process isn't running.
[INDENT]Jul 15 20:07:45 RavenWing cron[1026]: (CRON) INFO (Running @reboot jobs)
Jul 15 20:07:45 RavenWing CRON[1053]: (ceallred) CMD (/home/ceallred/Scripts/run_spideroak.sh > /home/ceallred/Scripts/SpiderOak.log 2>&1 &)[/INDENT]

It's seems like cron doesn't like the @reboot command....  Any other ideas?

Okay... Partially solved.  I'll mark this one as solved and start a new thread with the new issue.....

I think the answer was my encrypted home directory wasn't mounted when CRON was trying to run the script (stored in /home/username/scripts).   Moved to /usr/scripts and the job runs as expected.

So now it appears to be a spideroak issue.   Process starts, but by the time the boot process is finished, it's gone.   I'm guessing a crash for some reason....  New thread to ask about that.

Thanks for all the help!

---

