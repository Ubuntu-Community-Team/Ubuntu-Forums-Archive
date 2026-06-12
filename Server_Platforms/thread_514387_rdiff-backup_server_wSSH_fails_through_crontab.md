---
title: "rdiff-backup server w/SSH fails through crontab"
date: 2007-07-31
forum: Server Platforms
---

### Post by Acksys on 2007-07-31
Hi all,

I hope this is an appropriate forum in which to make this post. I inquired in the Absolute Beginners forum and received no replies.

I recently used the steps from [http://arctic.org/~dean/rdiff-backup/unattended.html](http://arctic.org/~dean/rdiff-backup/unattended.html) to setup a backup server to pull a nightly rdiff-backup of my laptop's installation over SSH. Everything worked  great until I tried to put the job in my crontab.

I set up a user called rdiff-backup with shell /bin/false to do this backup, per the instructions in the above article.

If I su to this user to perform the backup manually , it runs fine.

```

sudo
su -m rdiff-backup
rdiff-backup --exclude /mnt --exclude /tmp --exclude /proc --exclude /media --exclude /sys --exclude /lost+found fishie-backup::/ /media/sda3/backup/laptop-backup

rdiff-backup@acksys-studio:/var/log$ rdiff-backup -l /media/sda3/backup/laptop-backup

Found 2 increments:
  increments.2007-07-23T00:15:50-04:00.dir  Mon Jul 23 00:15:50 2007
  increments.2007-07-26T17:11:09-04:00.dir  Thu Jul 26 17:11:09 2007
Current mirror: Fri Jul 27 18:16:48 2007 
```

However, when I add it to rdiff's crontab

```

crontab -e -u rdiff-backup

# m h  dom mon dow  command
30 6 * * * rdiff-backup --exclude /mnt --exclude /tmp --exclude /proc --exclude /media --exclude /sys --exclude /lost+found fishie-backup::/ /media/sda3/backup/laptop-backup

```

and come back the next day, I get an error saying rdiff-backup "seems to have failed" when I check the backup with rdiff-backup -l.

```

rdiff-backup -l /media/sda3/backup/laptop-backup/
Fatal Error: Previous backup to /media/sda3/backup/laptop-backup seems to have failed.
Rerun rdiff-backup with --check-destination-dir option to revert directory to state before unsuccessful session.

```

When I run it again manually, it regresses the destination and backs up again, seemingly successfully (albeit with some innocuous-looking errors about special files).

Any ideas what could be causing this? /var/log/syslog.0 shows the cron job running on the backup server, and I don't see any obvious clues in any of the logs on either machine. I'd appreciate any ideas.

---

### Post by Mr. C. on 2007-08-01
The problem you are likely experiencing is due to the subtle differences between su and sudo.  While both change UIDs and GIDs, they have slightly different behaviors regarding setting the switched user's environment.

Because Ubuntu disallows running su to elevate privileges to root, you won't easily see the differences, and trying to explain the differences is probably more than you might want at this point.  Suffice it to say that the tutorial shows running **su**, but you have had to run** sudo su**, which ultimately results in different environment variables and shell settings when your commands are run.

You need to examine the file and directory permissions, and ownership, for your backup user, especially the .ssh directory and any files used by your rdiff-backup.  If you are not sure what permissions and owernship they should be, show an ls -l of all the relevant data.

MrC

---

### Post by Acksys on 2007-08-01
> **Mr. C. said:**
> you have had to run** sudo su**, which ultimately results in different environment variables and shell settings when your commands are run.

I actually enabled the root account on the backup server. The commands shown are verbatim what I type at the prompt.

> If you are not sure what permissions and owernship they should be, show an ls -l of all the relevant data.

I'll provide this info when I get home, thanks for the reply!

---

### Post by Acksys on 2007-08-02
As promised, here's the info for rdiff-backup's .ssh directory:

```

rdiff-backup@acksys-studio:/media/sda3/backup$ ls -al .ssh
total 24
drwx------ 2 rdiff-backup backup 4096 2007-07-22 18:35 .
drwxr-xr-x 4 rdiff-backup backup 4096 2007-07-23 00:15 ..
-rw------- 1 rdiff-backup backup  148 2007-07-22 18:34 config
-rw------- 1 rdiff-backup backup 1671 2007-07-22 18:08 id_rsa_fishie_backup
-rw------- 1 rdiff-backup backup  408 2007-07-22 18:08 id_rsa_fishie_backup.pub
-rw------- 1 rdiff-backup backup  884 2007-07-22 18:35 known_hosts

```

Any suggestions are appreciated!

---

### Post by Mr. C. on 2007-08-02
The standard reasons for cron jobs failing when the same command runs via command line are:

 1) PATH improperly set
 2) environment variable missing/different

Create a wrapper script that outputs your environment variables into some file, and then calls your rdiff-backup script.  Call that script from cron.  Examine the environment variables and compare them to those set when you run manually.

Cron commands run with a different environment than your command line commands.

Additionally, you may want to increase the verbosity of rdiff-backup.  Have you examine its logs?  You can also increase the verbosity for the terminal output, which will get sent via email when cron is completed.

Hope this helps a bit.
MrC

---

### Post by Acksys on 2007-08-14
Well, I finally finished moving back to college and got settled down, so I could tackle this very important issue once again.

Thank you very much, Mr. C, for your suggestions. I created a wrapper script and struggled with it all day yesterday with no success. I checked the PATH variable, and it was okay. There were a lot of environment variable differences between the su and crontab sessions, but none of them turned out to be the culprit.

I'm honestly not sure what the problem was, but the script started working like a charm when I started redirecting both standard output and standard error to a special log file for closer examination.

I've attached my working script for others to use (I know it could be more robust and elegant). Would anyone care to take a quick look and guess at what my problem was? I'd like to satiate my curiosity.

Thanks again for the help.

---

### Post by Mr. C. on 2007-08-14
I noticed that your cron job did not test the exit result of rdiff-backup. Its might be better to exit your script when any failure occurs (vs. continuing operations as it does now).

There is nothing obviously wrong with your script (other than what I just mentioned).  Its not clear to me why redirecting STDOUT and STDERR would allow operation under cron to start working.

I'm glad things are working for you though.

MrC

---

### Post by Acksys on 2007-08-15
That's an excellent suggestion. This is actually the first bash script I've written, so I did it in a hurry. I'll change it soon.

---

