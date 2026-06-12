---
title: "Getting my Shell Script to Run on Cron.daily"
date: 2010-09-30
forum: Server Platforms
---

### Post by Vegan on 2010-09-30
My backup script works fine after some effort to get it where I wanted it. So the script is fine when I run it.

sudo bash backup.sh

now I have a sym-link to /etc/cron.daily but I do not see any new backups

what am I doing wrong?

---

### Post by CharlesA on 2010-09-30
I don't use /etc/cron.daily for my scripts, but instead just throw them in a crontab with something like this:

```
# Backup RAID Array incrementally daily at 2am
0 2 * * * /home/charles/scripts/backup.sh > /dev/null 2>&1
```

Have you tried doing that?

---

### Post by SeijiSensei on 2010-10-01
> **Vegan said:**
> sudo bash backup.sh

Does the top line of the file read "#!/bin/sh" or "#!/bin/bash"?  These tell the script processor what program to use to execute the script.  Since you need to invoke bash to run the script manually, I'm guessing you don't have a line like this at the top of the script.

This convention isn't limited to shells.  Perl scripts usually start with "#!/usr/bin/perl" for the same reason.

I've moved away from putting everything in /etc/crontab over the years except for scripts that need to run more often than hourly.  Even then I've started moving the crontab entries for those types of processes into /var/spool/cron/root.

---

### Post by Vegan on 2010-10-01
```

#!/bin/sh
#backup MySQL to a date named file
mysqldump -u root -p********** --all-databases > "/public/backup/`date +%Y%m%d`.sql"
tar -cf /public/backup/`date +%Y%m%d`.tar /www
cd /public/backup
# the -9 option for gzip uses the maximum compression possible, slow
gzip -9 -q  *.sql
gzip -9 -q *.tar
chmod 777 *.*
#remove older backups so as not to consume infinite space
ROTATE=90
STALE=`date --date="$ROTATE days ago"`
rm -f "/public/backup/$STALE.sql.gz"
rm -f "/public/backup/$STALE.tar.gz"

```

---

### Post by Vegan on 2010-10-01
I tried the crontab angle as suggested, maybe that gets the ball rolling?

Not sure why cron is failing, that seems to be a defect perhaps?

I expect my s-link to be fine, the script is chmod +x etc

---

### Post by Vegan on 2010-10-01
crontab -l shows nothing there

---

### Post by SeijiSensei on 2010-10-01
Maybe the cron daemon isn't running?  If you type "ps ax" do you see an entry for cron?

Try "sudo service cron restart" and see if that helps.  (On older distributions that don't use the new "upstart" system, you might need to enter "/etc/init.d/cron restart" instead.)

The "crontab -l" command only looks to see if there are files in /var/spool/cron for the current user.  It won't report on scripts run from /etc/cron.daily, etc.

---

### Post by Vegan on 2010-10-01
I already looked to make cron was operating, it is.

  671 ?        Ss     0:00 cron

So I will come back here tomorrow and let e1 know what happened over night.

---

### Post by Vegan on 2010-10-02
No new backups, still compelled to be manual.

---

### Post by SeijiSensei on 2010-10-02
For some strange reason [scripts with a dot and an extension in their filenames don't run]("https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022") from /etc/cron.daily|weekly|monthly.  I'd bet that's the reason for your problem. (It's marked as WONT FIX upstream at Debian, and the Ubuntu packagers have decided to follow Debian's lead. It has something to do with how dpkg works.)

Still the whole business with anacron and cron has generated a lot of confusion and bug reports.  Just do a search for 'ubuntu cron.daily' and you'll see what I mean.  Try removing the dot from the script filename and recreating the symlink. Let's see what happens.

---

### Post by CharlesA on 2010-10-02
Wow that's really annoying.

Can you do a symlink with a different filename?

---

### Post by Vegan on 2010-10-03
I will try removing the .sh which is the standard naming convention for a shall script

so I will try backup with no extension at all

still i have been on the merry-go-round for god knows how long

I noticed other items in /etc/cron.daily have no extensions at all. They are simply filenames and are not even linked or anything.

---

### Post by koenn on 2010-10-03
"extensions" have no special meaning on Unix/Linux - the system just sees a filename. Especially for shell scripts, what makes a script a script, is the #!/path/to/interpreter statement and the +x permission rather than the extension (contrary to, eg, Windows) 

the .sh "extension" is completely arbitrary, and, imo, is useless in scripts. scripts behave as commands, and are preferably named after the action they perform.  It makes more sense, and is more user friendly imo, to execute a script by running eg 'backup' (or 'synchronize' or 'getdiskfreespace' or whatever) than it is to call 'backup.sh' (or 'synchronize.pl', 'getdiskfreesoace.py', 'move.bin', etc.)


It *is* weird, however, that cron would have a problem with filenames that have dots in them.

---

### Post by Vegan on 2010-10-03
I agree, and once again I am cuing up the Stones - Can't Get No Satisfaction.

This is a fresh install of Ubuntu so I do not get it.

Must be a defect.

Scripts are valid and cron is a standard, what gives?

---

### Post by koenn on 2010-10-03
cron has been know to fail when it doesn't know what to do with the output of its jobs.
typically these are mailed to root or whoever owns the process; maybe that's part of your problem.
you might get around this by redirecting all output to /dev/null - see CharlesA's crontab 

(Stones : You can't always get what you want, but you might get what you need)

---

### Post by CharlesA on 2010-10-03
Did it work when you put it in just a normal crontab?

You seem to just want to run it in cron.daily instead of trying other means.

I've had shell scripts (with the .sh extension) running fine in crontabs since 9.10.

> **koenn said:**
> cron has been know to fail when it doesn't know what to do with the output of its jobs.
typically these are mailed to root or whoever owns the process; maybe that's part of your problem.
you might get around this by redirecting all output to /dev/null - see CharlesA's crontab 

(Stones : You can't always get what you want, but you might get what you need)

I added the "> /dev/null" since I was sick of getting emails if the script failed to run. It's a nice thing to do to see if the script is running correctly or not.

I've got all my scripts set to write errors to a log file should they fail, so it seemed a bit redundant.

---

### Post by koenn on 2010-10-03
> **CharlesA said:**
> 
It's a nice thing to do to see if the script is running correctly or not.

true, but it only works if there's a correctly configured MTA on the system.

in a case like the OP's, if dropping the output on the floor solves the problem, at least you have a diagnosis

---

### Post by CharlesA on 2010-10-03
> **koenn said:**
> true, but it only works if there's a correctly configured MTA on the system.

in a case like the OP's, if dropping the output on the floor solves the problem, at least you have a diagnosis

Indeed. I found that redirecting the output, including errors to a file helps greatly in troubleshooting and debugging.

---

### Post by Vegan on 2010-10-04
Interesting is the this AM I see 2 files in the designated backup folder. They were make 6:27 AM which is fine, I do not care what time, as long as its done as desired, daily.

Yesterday I removed all backups to the Windows box as I put them in a USB disk so they would be handy in case they are needed.

It seems the rename job and new ln seems to fix it.

Sure seems that the people managing Linux should be aware of my issues as thus is not the way it supposed to work.

I should be able to use backup.sh so that I can know its a shell script as compared to backup.php which is a PHP script etc. I like this convention as it allows me to use the right programming mindset.

Linux should be filename agnostic, I should be allowed to name my files as anything I want.

tar uses .tar and gzup adds .gx to the backups as used. I backup my /www folder so that in case I need to restore.

So one is tar.gz and one is sql.gz, what is the problem?

I could add >/dev/null but that takes away from the manual invokation I like should I chode to change the script, which I will admit is ugly but it works

---

### Post by Vegan on 2010-10-04
One other thing I did to the script to graunch the situation was

chmod 777 backup
chown root:root backup

this seems to be where I went wrong, the script was previously under my login name account.

I wonder if that oversight was my problem?

---

### Post by SeijiSensei on 2010-10-04
If you have a Launchpad account, perhaps you might want to leave a comment in the [bug thread]("https://bugs.launchpad.net/ubuntu/+source/debianutils/+bug/38022") I cited above.  Though it sounds like the Debian developers have pretty much made up their minds about this, perhaps the Ubuntu developers can be convinced to diverge from upstream in this case.

---

### Post by Vegan on 2010-10-04
I have consolidated all I have learned from my experience here into a brain cell.

---

