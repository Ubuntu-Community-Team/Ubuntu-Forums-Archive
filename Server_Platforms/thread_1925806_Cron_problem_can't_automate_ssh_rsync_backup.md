---
title: "Cron problem: can't automate ssh rsync backup"
date: 2012-02-15
forum: Server Platforms
---

### Post by wall_e on 2012-02-15
Hello all.

I am trying to automate a cron job for backup.

The command I have uses rsync and ssh to backup my ubuntu home folders to a mac elsewhere on my network.

SSH is setup so the machines can talk to each other without needing to provide credentials -  key pair.

The command runs fine if I run it by hand or from within webmin as a cron job - using run now.

However it won't run when automated or by schedule.

I am quite new, please be gentle with me. lol

Here is the output of root users crontab:

```
59 23 * * * rsync -a -e "ssh -c arcfour256 -i /home/elmo/.ssh/id_dsa" /home ag246@3.9.56.3:/Volumes/ELMO_BACKUP       #ELMO BACKUP RSYNC
```

---

### Post by Cheesehead on 2012-02-15
Root crontabs have an additional Username field.
```
* * * * * Username Command
```

The output from /var/log/syslog can also help diagnose the problem.

Generally, good practice is to move complex commands into a script, where you can comment and annotate, and add tests and fault protection/correction. There is a real risk that six months forward you may not remember anymore what this command was supposed to do, why, or what all those fields mean.
```
# This is the elmo backup script
# It backs up elmo every night
# This script is triggered by a cron job daily at 23:59

# ssh cipher and identity file
ssh_command='"ssh -c arcfour256 -i /home/elmo/.ssh/id_dsa"'

# backup origin and destination
origin="/home"
destination="ag246@3.9.56.3:/Volumes/ELMO_BACKUP"

rsync -a -e "$ssh_command $origin $destination"
```

Does it really need to run as root? Can it run as user elmo instead?

---

### Post by wall_e on 2012-02-15
Thanks for the reply cheesehead.

I've tried to run the command as me (elmo) but it requires sudo otherwise rsync spits out a bunch of permission fails, presumably because I am backing up other home folders too. This is why I ran it as root. For some reason, probably through ignorance, I seem to be under the impression rsync is often required to run as root in order to avoid this?

I created a shell script based on the example you kindly provided above, but I get an rysnc syntax error which is strange because the script looks good to me.

Unfortunately looking at syslog doesn't seem to shed any light, there is no error or report of failing at the time the cron job is supposedly to run.

---

### Post by sudodus on 2012-02-15
My little contribution:

The environment of ***cron*** is very basic, so you should provide full paths to all commands for example
```
/usr/bin/rsync
``` and
```
/usr/bin/ssh
```

---

### Post by wall_e on 2012-02-15
Thanks for the input.

I've tried modifying both crontab and the shell script with the full path of each, but still nothing.

---

### Post by Cheesehead on 2012-02-15
> **wall_e said:**
> I've tried to run the command as me (elmo) but it requires sudo otherwise rsync spits out a bunch of permission fails

Well, that makes sense.

I systematically debug cron srcipts in this sequence:
Did cron activate the script?
  If not, it's a cron or crontab issue.
  If so, it's a script error.

Try a simple crontab:
```
* * * * * root /path/to/testscript
```

And a simple testscript. This one simply sends a success message to /var/log/syslog:
```
logger -i "Cron successfully ran the testscript."
```

Your script can include all kinds of tesing and error-catching and debugging. That's why it's great as a script instead of a cryptic crontab line.

```
logger -i "Starting the script."

# Your code here

if [ $? -eq 0 ]; then
  logger -i "The script finished sucessfully"
  exit 0
else
  logger -i "Uh-oh. Script error"
  exit 1
fi
```

My expertise is cron/crontab instead of rsync, so I'll defer to an rsync guru. The most likely cause of failure is a syntax error somewhere in the script. ([hint]("http://www.linuxquestions.org/questions/linux-general-1/bash-script-to-rsync-remote-dir-with-options-666334/"))

---

### Post by wall_e on 2012-02-16
Thanks again cheesehead.

The problem looks like its on the cron/crontab side of things because I just tried the logger test and no entries appear in /var/log/syslog

Its strange because I've not messed with any of this, Im running 10.04.3 but with the addition of AFP, Samba and Webmin it is basically vanilla.

EDIT: When I run the script manually I get the message "Cron successfully ran the testscript."

I've checked there is no **/etc/cron.allow or **[B]/etc/cron.deny.
[/B]

---

### Post by wall_e on 2012-02-16
SOLVED!

Feeling a little stupid now.

First I restarted cron, should have done this before, then what do you know.... cheesehead's test script starting showing in the syslog.

It seemed unhappy about the 'root' user being defined as part of the crontab entry.

Since I was editing using crontab -e (I believe this is entries for root anyway), I removed the 'root' entry and the test script began working.

I can now run my backup every night!

Thanks for all the help guys, you taught me a lot in a very short space of time :D

---

### Post by sudodus on 2012-02-16
> **wall_e said:**
> SOLVED!
...
Since I was editing using crontab -e (I believe this is entries for root anyway), I removed the 'root' entry and the test script began working.
...
I'm glad you made it work, but you should know that ```
crontab -e
``` is editing a cron table running cron with your user id (not with root id alias superuser). See ```
man crontab
```

---

### Post by wall_e on 2012-02-17
Thanks for the info.

I was just going by what I read here:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

But I can now see what you mean.

---

