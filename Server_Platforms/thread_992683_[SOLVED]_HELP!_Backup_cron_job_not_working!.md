---
title: "[SOLVED] HELP! Backup cron job not working!"
date: 2008-11-25
forum: Server Platforms
---

### Post by Null_Pointer on 2008-11-25
I haven't had any responses over at the Zimbra forums, so I'm trying here.

I have Zimbra ZCS 5.0.10 running in an Ubuntu 8.04 virtual machine on an older Windows 2000 server. In order to backup Zimbra each evening, I've setup a cron job to run a script called zimbraNightlyBackup.sh:

```
#!/bin/bash

sudo -u zimbra /opt/zimbra/bin/zmcontrol stop
tar -cvf /media/zimbraNightlyBackupCache/zimbraNightlyBackup.tar.gz /opt/zimbra
sudo -u zimbra /opt/zimbra/bin/zmcontrol start
```

zimbrNightlyBackup.sh is in /root/cronscripts/. "/media/zimbraNightlyBackupCache/" is a CIFS automounted samba volume on the W2K server. It works great when I run it from the console as root, but doesn't seem to work right when run as a cron job.

When I run the script from the console as root, the resulting tar.gz winds up being about ~800MB, and mail services shutdown and come back up properly.

When run as a cron job, it takes down mail services properly, creates a ~200MB tar.gz, and then never starts mail services again. 

The key weirdness here is how it works just fine when at the console as root via "sudo -i", but not as a cron job.  I'm probably missing something obvious. Any ideas?

- Joe

---

### Post by Philio on 2008-11-25
Did you set this up as a cronjob for root or for your normal user account?

If it's under your user account you could possibly have a permissions problem.

User crontab -l to look at the crontab for both your user account and root and make sure.

---

### Post by wizard10000 on 2008-11-25
Everybody does this differently but I put systemwide cron jobs in /etc/crontab instead of a user's crontab - it just seems easier to me.  You can stick it in there and then just assign the job to the root account instead of using sudo.

Give it a try -

---

### Post by MJN on 2008-11-25
Firstly, I am assuming you are running this cron job as root. If not, why not?
 
You need to step into the script to see where it is stalling as, given you are ending up with a 200MB backup file, you know it is stopping Zimbra and at least making a start on the backup.
 
Presumably you don't get any mail output from it? Does **ps aux** show the tar task still running? Redirect the output of tar to a file then you can see how far it is progressing (i.e. stick **>> /logfile** on the end).
 
Mathew

---

### Post by Null_Pointer on 2008-11-25
First of all, thanks for the replies...I'm disenchanted with the Zimbra forums.

Philio: Yep, I set this job up while at the console as root via "sudo -i". "crontab -l" does indeed reveal that this cron job is running as root, not my user account. I checked that already, but thanks for the good advice.

Wizard: If I were to put cron jobs in /etc/crontab?  I've never used this method before. How would assign that job to a certain user as you've suggested.  I don't think this will solve my problem, but I like the convention.

MJN: It doesn't look like tar is still running, using "ps aux | grep tar". I will try out your logfile technique, but what logfile does this route to? syslog? messages? dmesg?

Thanks all,

- Joe

---

### Post by Null_Pointer on 2008-11-25
Wizard: I see how /etc/crontab works.  Very cool. I'll test my task via this method and see how it goes.

- Joe

---

### Post by HermanAB on 2008-11-25
The cron environment is very limited.  Always use the full paths when you spawn programs in a cron script.  To run the script every day, simply drop it into /etc/cron.daily - you don't need to mess with crontab.

Hope that helps!

Herman

---

### Post by Philio on 2008-11-25
It shouldn't really many an difference if you install it via root or /etc/crontab

Personally I find using crontabs for individual users a bit more organised (have separate crontabs for separate users/vhosts), but it's down to personal preference at the end of the day!

It sounds like your backup is hanging for some reason, however don't have a clue why it would run correctly via shell but not via cron, never come across this before! Your using bash as well in your shell script so it should run in an identical fashion. There can sometimes be issues between different shells but it doesn't seam likely in your case.

---

### Post by Null_Pointer on 2008-11-25
Herman: Cool idea, except that something like this where I have to have it run a few hours prior to when the tape system runs, it doesn't seem like a good plan.  cron.daily looks like it's set to run at like 5pm each day.  Plus, I want to minimize CPU utilization during the mail shutdown / backup / mail startup because the server is kind of an old pig.  Hopefully, someday soon I can get Ubuntu server on there as the base OS and virtualize  their Windows sever. ;) I WILL use your suggestion, however, for other smaller daily tasks. Thanks!

Philio: Right! I can't figure it out! It SHOULD be running just as it would from the console. I'll take your advice on absolute paths and perhaps specify the path to the tar binary explicitly.

I'll try some more stuff tonight and post some results tomorrow, if I remember.

- Joe

---

### Post by MJN on 2008-11-25
> **Null_Pointer said:**
> I will try out your logfile technique, but what logfile does this route to? syslog? messages? dmesg?It'll just end up in the text file specified ('/logfile' in this case).
 
Mathew

---

### Post by Null_Pointer on 2008-11-25
MJN: Aha... I see. Thanks.

- Joe

---

### Post by Null_Pointer on 2008-11-25
Alright, I have some diagnostic info...and it's weird!!!

I modified the script as follows. I'm directing output for the tar operation to /tarlogfile. Instead of tarring directly to the samba share (media/zimbraNightlyBackupCache), I'm sending it to a local location first (/root/zimbraNightlyBackupCache).  Then I start mail services back up.  Then I gzip the tar.  Then I move it to the samba share.

```
#!/bin/bash

# shutdown zimbra mail services
sudo -u zimbra /opt/zimbra/bin/zmcontrol stop
sleep 5

# tar zimbra folder to backup cache
tar -cf /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar /opt/zimbra >> /tarlogfile
sleep 5

# startup zimbra mail services
sudo -u zimbra /opt/zimbra/bin/zmcontrol start

#gzip the big tarball
gzip /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar

#move it to the samba share on w2kserver
mv /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar.gz /media /zimbraNightlyBackupCache/zimbraNightlyBackup.tar
```

Once again, I'm getting different behavior from cron than I do at the console. When I just run "tar -cf /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar /opt/zimbra >> /tarlogfile" from the console, I wind up with a tar file that is well over 2GB.  I also see verbose output from tar telling me how sockets will be ignored (normal). In contrast, when the cron job runs, I get a tar file that is about 500MB and there is absolutely nothing in /tarlogfile.

However, the mail services ARE coming back up now on their own after the tar operation "completes".

I just don't see how running from console gives me a file size of over 2GB, while running from cron gives me only 500MB.  Why would it make a difference???

What the frick?!?! :confused:

- Joe

---

### Post by Null_Pointer on 2008-11-25
While on the topic, a friend just sent me this article on bash debugging: [http://www.linux.com/feature/153383](http://www.linux.com/feature/153383)

Cool! Though I don't know if it will be particularly useful in this situation.

- Joe

---

### Post by MJN on 2008-11-26
> **Null_Pointer said:**
> tar -cf /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar /opt/zimbra >> /tarlogfile> [...] and there is absolutely nothing in /tarlogfile.Are you that is not because you have dropped the -v verbose logging option?
 
Mathew

---

### Post by Null_Pointer on 2008-11-26
MJN: Don't know! How is verbosity set?  I haven't explicitly set it to any level, AFAIK.

- Joe

---

### Post by Null_Pointer on 2008-11-26
This mail archive from osidr.com seems to provide a clue: [http://osdir.com/ml/redhat.release.guinness/2002-09/msg00042.html](http://osdir.com/ml/redhat.release.guinness/2002-09/msg00042.html)

> Instead, run your job iteratively using the batch commmand. It provides the exact same environment as cron. Also, add an env commmand so you can compare what the difference is between what works from the console vs. what doesn't work from cron. Also, be advised that cron does not have access to a terminal, so if your job is presuming access to one, that could be (part of) your problem.


Sounds like cron has no terminal access.  That could certainly be the problem. So, now what?  I can't believe that I'm just SOL.

- Joe

---

### Post by MJN on 2008-11-26
> MJN: Don't know! How is verbosity set?  I haven't explicitly set it to any level, AFAIK.With the -v flag!

e.g. tar -c**v**f /root/zimbraNightlyBackupCache/zimbraNightlyBackup.tar /opt/zimbra >> /tarlogfile

Mathew

---

### Post by Null_Pointer on 2008-11-26
> With the -v flag!

DOH! Thanks!

- Joe

---

### Post by Null_Pointer on 2008-11-26
Oh man! I think I found the holy grail of cron script instructions: [http://argray.com/unixfaq/cron.shtml#scripts](http://argray.com/unixfaq/cron.shtml#scripts)

Looks like there's more involved than I anticipated. I am, however, determined and WILL get this working.

- Joe

---

### Post by Null_Pointer on 2008-11-26
Follow up:

I never did get MY script working, but I found one that's a zillion times better: [http://www.osoffice.de/howto/yet-another-backup-script-for-zimbra-community-edition-groupware-server.html](http://www.osoffice.de/howto/yet-another-backup-script-for-zimbra-community-edition-groupware-server.html).  It's so advanced, it actually has an install feature for setting it up, including making the crontab entries.

And by examining that script, I believe I may have found the problem with my own. The generated crontab entries from the install script:

```
00 20 * * 1     /bin/bash     /root/cronscripts/zmbac.sh -f > /var/log/zim_backup.log 2>&1
00 20 * * 2-7   /bin/bash     /root/cronscripts/zmbac.sh -d >> /var/log/zim_backup.log 2>&1
```

Notice the "/bin/bash" before the actual command.  "/bin/bash" has to be included BEFORE calling the script. I have not verified this, but it makes sense and is congruent with other bits of information I found on the internets while trying to solve this problem. Good to know!!!

This is root's crontab above, of course.

- Joe

---

### Post by MJN on 2008-11-27
> **Null_Pointer said:**
> Notice the "/bin/bash" before the actual command. "/bin/bash" has to be included BEFORE calling the script. I have not verified this, but it makes sense and is congruent with other bits of information I found on the internets while trying to solve this problem.You're stabbing in the dark now and getting confused in the process!
 
The /bin/bash prefix to the script merely dictates that the BASH command interpreter will be used to execute the commands in the script. This is no different than including a hash-bang line at the beginning of the script - as you had done with the inclusion of #!/bin/bash as the first line.
 
Still, you're up-and-running now which I guess loosely justifies the [SOLVED] tag!
 
Mathew

---

### Post by Null_Pointer on 2008-11-27
Point taken...and appreciated.

- Joe

---

### Post by Null_Pointer on 2008-12-23
Just wanted to provide follow up for anyone that stumbles across this.

Two things contributed to the eventual success of my script:
[LIST=1]
[*]Explicitly setting environment variables in the head of the script
[*]rsyncing the "source" folder to a temporary location before tar/gzip
[/LIST]

---

### Post by mowgliee on 2009-05-31
my symptom is a bit quirkier than yours:
if i leave crontab w/ shell=/bin/sh, tar fails midway.
if i change crontab to shell=/bin/bash, tar fails midway but at later point.
if i add > /tmp/tarlogfile at end of tar command, tar succeeds 100% and log file proves it!

but i dont want or need that log file; plus i want to know the true cause of this problem.  otherwise i cant rely on other backups being thorough backups (i was just testing a small list of files to get the above symptoms; real backups will be several hundred megs or a few gigs).

so anyone have any idea why it would work w/ redirecting output but not otherwise?

irony is i cant tell when it fails b/c it only fails if i dont redirect the output!

ps i chose tarlogfile as my filename too, before seeing your choice.  funny how distinct minds yet think alike.

---

