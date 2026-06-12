---
title: "Cron won't run rsync job"
date: 2011-03-30
forum: Server Platforms
---

### Post by damo12 on 2011-03-30
[FONT="Comic Sans MS"]I am running a headless Ubuntu server accessed through Webmin.  The server is running 10.4.2 64 bit version.

I have a number of cron jobs including a simple back-up job which is:

```
rsync -av /media/server/ /media/backup/backup/
```

All of the other jobs run fine but for some reason this job which is scheduled to run each day at midnight does not run.  If I SSH into the server and run the job manually it works fine.

The output of 'crontab -l' is:

@daily rsync -av /media/server/ /media/backup/backup/
11 3 * * * /etc/webmin/package-updates/update.pl
@daily tar czf /media/backup/serversystem.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/media --exclude=/sys /
@reboot  inadyn --username ********** --password ********** --update_period_sec 600 --alias **********
@daily /etc/webmin/backup-config/backup.pl 12978522112842


The output of 'crontab -e' is:

Error opening terminal: unknown.
crontab: "/usr/bin/sensible-editor" exited with status 1


Can you please advise where I am going wrong with this.

Thanks in advance for what I'm sure is a straight forward question.
[/FONT]

---

### Post by Paddy Landau on 2011-03-30
Redirect output into a file so that you can find what is happening. In other words, for your command put this:
```
rsync -av /media/server/ /media/backup/backup/ >>*[path]*/rsync.lst 2>&1
```Replace *[path]* with a path that you know rsync can write to. Then you can find out what the error is.

You have three commands running at midnight every day, at least two of which are disk-intensive; they might cause quite some overhead on the machine. Maybe you want to reschedule them one after the other instead of simultaneously.

Also, please [FONT=Comic Sans MS]don't write in unusual scripts[/FONT]. It makes it hard for some people to read. It would have helped to put the output of crontab -l in a code section, too. Thank you.

---

### Post by DaithiF on 2011-03-30
Sounds like this issue: [http://ubuntuforums.org/showthread.php?t=825242](http://ubuntuforums.org/showthread.php?t=825242)

---

### Post by damo12 on 2011-03-30
Thanks for the suggestion Paddy, I have modified the time of this job so it now runs at 2:00am each day.  My 'crontab -e' now shows:

```
0 2 * * * rsync -av /media/server/ /media/backup/backup/ >>/media/cron_log/rsync.lst 2>&1
11 3 * * * /etc/webmin/package-updates/update.pl
@daily tar czf /media/backup/serversystem.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/media --exclude=/sys /
@reboot  inadyn --username ********** --password ********** --update_period_sec 600 --alias **********
@daily /etc/webmin/backup-config/backup.pl 12978522112842
```

I have checked and I can certainly write to /media/cron_log/ so i will post the results tomorrow if it fails.

Sorry for the font, I am dyslexic and find Comic Sans an easier font to read, it never occurred to me that other people might struggle with it.  I'll bear that in mind for future postings.


DaithiF, thank you for your suggestion.  My current crontab reads:

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

I take it you mean that if this fault continues I should just add the command at the top of this file?  Sorry for asking an obvious question but to be honest I'm still quite new to Linux and Ubuntu.

Thanks again for your help.

---

### Post by DaithiF on 2011-03-30
> **damo12 said:**
> I take it you mean that if this fault continues I should just add the command at the top of this file?  Sorry for asking an obvious question but to be honest I'm still quite new to Linux and Ubuntu.

err, no ... i'm confused how you came to that conclusion ... did you read my post from that thread i linked?

I'm saying that in your crontab, (ie. crontab -e), to add the line MAILTO="" at the top of the file, before you get to the actual commands you want to run.

if the issue i am referencing is the issue you are encountering then you will find that paddy's suggestion of redirecting output to a logfile will cause the job to run successfully, for the reason I gave in the post I've referenced.

---

### Post by damo12 on 2011-03-30
Sorry DaithiF, I read the link you gave and mis-understood what you meant.  Your solution was to put MAILTO="" at the top of the crontab, I thought you meant to put that at the top of the crontab file.

Fingers crossed it will be sorted.  Either way I'll post tomorrow marking the post at Solved or listing the output of the output file.

---

### Post by Paddy Landau on 2011-03-30
> **damo12 said:**
> Sorry for the font, I am dyslexic and find Comic Sans an easier font to read
Gosh, and I never realised anyone would find it easier! Sorry from my side, too. It shows how different people can be.

Let us know tomorrow whether it works and, if not, what your new log file says.

You could try setting it to run in the next few minutes, so you don't have to wait until tomorrow.

---

### Post by damo12 on 2011-03-30
Thank you so much for all of your help.  I tried a test sync and it worked fine with the output sent to the text file.  I can't believe it was that simple.

thanks again.

---

### Post by Paddy Landau on 2011-03-31
Excellent, I'm glad you solved that.

If you don't need the output, redirect the output to a *null* file as follows. I've highlighted the changed code.
```
rsync -av /media/server/ /media/backup/backup/ **[COLOR=DarkRed]>/dev/null[/COLOR]** 2>&1
```And, I've just realised it can be simplified further:
```
rsync -av /media/server/ /media/backup/backup/ **[COLOR=DarkRed]&>/dev/null[/COLOR]**
```

---

### Post by RedScourge on 2011-05-03
Just a note about using /etc/cron.hourly daily weekly monthly, or any other  cron situations where you are using run-parts (whether you realize it or  not):

I noticed that run-parts on Debian and Ubuntu based systems seems to  disallow using anything but lowercase, uppercase, numbers, underscore,  and dash in script names. IT DOES NOT ALLOW DOTS! I  spent many days figuring this one out, until I found it in the man page for run-parts. I came from RedHat based  systems where this seemingly arbitrary restriction does not exist.

To fix this:

Anywhere you use the run-parts command (such as in /etc/crontab) change "run-parts --report" to "run-parts --report  --regex='(^[a-zA-Z0-9.\  _-]+$)'" or so, and that way you can do dots and/or spaces again. You can  increase the complexity of the regex and allow more options, or perhaps  go with something not very restrictive at all, such as --regex='(.*)'  which should in theory allow any file name, though I have not tested this. 

If you do NOT want some files in these folders to execute, you'd be better off removing their execute permission, making them solely contain comments, or having seperate folders such as /etc/cron.custom and /etc/cron.never to store them in, than relying on this strange feature, so you are less likely to cause yourself or others unnecessary pain in the future.

---

### Post by Paddy Landau on 2011-05-04
> **RedScourge said:**
> ... where you are using run-parts
Thank you for that. I had not come across run-parts before.

From its manual:
> If  neither  the --lsbsysinit option nor the --regex option is given then the names must consist entirely of upper and lower case letters, digits, underscores, and hyphens.We have been warned!

---

