---
title: "Strange Cron script behaviour"
date: 2007-08-15
forum: Server Platforms
---

### Post by kwambus on 2007-08-15
Hi,

This is an odd one but I have searched high and low and can find nothing to help so this is a long shot.

I made a bash script to "tar" a directory and its contents for backup purposes. This works absolutely fine when run from the command line. However when I run it is a Cron job it just stops around 4 minutes in, no errors in any log file, the script even generates a log file to and no errors in there either. The Cron job is run by root and executes perfectly for thie first few minutes then just disappears from the task list with no errors..

I decided it may be my scripting so I created a simple script to "cp -R" the same directories to another location on the hard disk. Again this works fine from the command line, but curiously stops executing with no errors anywhere 3 or 4 minutes in to the Cron job.

I have disk space, all privileges are correct... Anyone ever had a similar problem? or perhaps any suggestions on how I can debug these mysterious "halts"?

---

### Post by a9k on 2007-08-17
Have you tried doing the cp -R as [COLOR="Blue"]cp -vR > /root/cp-log[/COLOR] ? 

Maybe the copy stops on the same file or directory every time.

I had similar trouble with rsync once when one directory had permissions set to 000 (no access for anyone). Root could cd into the directory in bash but not with rsync.

---

### Post by kwambus on 2007-09-26
I found the solution to this problem and I just felt compelled to share it:

Cron was indeed failing or bombing out of the tar script every time at about 800mb. The final file should have been in the region of 30 gig. 

After weeks of head scratching and trying virtually everything I could think of; environment variables, different users, etc, etc... I stumbled across an obscure thread about CygWin which shows a user with a similar problem:

[http://cygwin.com/ml/cygwin/2006-06/msg00632.html](http://cygwin.com/ml/cygwin/2006-06/msg00632.html)

Believe it or not installing an MTA (in my case apt-get install sendmail) did indeed solve the problem! I can't believe it, even though my script never calls an MTA or sends email in any way Cron was seemingly checking for the presence of one and bombing out if it did not find it.

So there you go, a very obscure solution to my problem. I hope this will save others the headache I had as my script was the same on several Ubuntu Server installations.

I would greatly appreciate if anyone can shed light on this strange behaviour, standard vanilla server install of Fiesty, only being used as a backup server.

---

### Post by koenn on 2007-09-26
> cron will try to email you the output of a job if it's not redirected into a file, even if the output is empty. [http://cygwin.com/ml/cygwin/2006-06/msg00632.html](http://cygwin.com/ml/cygwin/2006-06/msg00632.html)

man cron: >        cron then wakes up every minute, examining all stored crontabs,  check ing  each  command  to  see  if it should be run in the current minute.
       When executing commands, **any output is  mailed**  to  the  owner  of  the  crontab 

So probably cron just quits its job if it can't find an MTA, but you might be able to work around it by redirtecting output to a file, as a9k suggested. 

It shouldn't really be an issue, as most distro's have an MTA installed by default - it's kind of the standard report tool on Unix : programs just drop msgs in root's mailbox if anything is worth mentioning. 

You might want to inquire with the ubuntu server devs about having an MTA included.

---

### Post by kwambus on 2007-09-27
Interesting stuff Koenn.

Indeed this does seem to be the case. I wonder if it only effects the more intensive Cron jobs, or most all of them. Either way there are no errors to reflect this anywhere and I think it should be rectified some how. I shall post a bug report and see what happens. Either way it's going to be on server setup list now!

Thanks and resolved.

---

### Post by Gouki on 2008-01-08
Interesting. The same thing was happening to me with UbuntuIRCStats.org.

Basically, it's just a bot collecting data and this same date gets parsed a script written in C. When cron launched the script, only half the channels got their statistics.

Instead of installing an MTA, I just flushed the output to /dev/null 2>&1

---

