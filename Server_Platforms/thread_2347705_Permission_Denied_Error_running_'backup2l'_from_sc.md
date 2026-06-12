---
title: "Permission Denied Error running 'backup2l' from script - runs fine from command line!"
date: 2016-12-27
forum: Server Platforms
---

### Post by agarwaldvk on 2016-12-27
Hi Everyone


I have been trying to test run my scheduled backup process using the 'Backup2l' tool.

With small modifications to the initial configuration file, I have been able to get it going. It runs ok and generates the backups as expected when the command is issued at the terminal like so :-

backup2l -b

I wanted to have it run using a script file but in doing so, it came up with the permission denied error. The error screen dump has been reproduced here for your immediate reference


```

agarwaldvk@MyHomeServer:~$ ./backuptest.sh
backup2l v1.5 by Gundolf Kiefer

Wed Dec 28 12:41:32 AEDT 2016

/usr/sbin/backup2l: line 340: /sharedfiles/backupdata/all.lock: Permission denied
Running pre-backup procedure...
  pre-backup: nothing to do

Removing old backups...

Preparing differential level-1 backup <all.31> based on <all.3>...
find: 'TMP.all.skipped.dirs': Permission denied
/usr/sbin/backup2l: line 640: TMP.all.list: Permission denied
cat: TMP.all.skipped.dirs: No such file or directory
cat: TMP.all.skipped.files: No such file or directory
/usr/sbin/backup2l: line 646: TMP.all.skipped: Permission denied
/usr/sbin/backup2l: line 652: TMP.all.diff: Permission denied
grep: TMP.all.diff: No such file or directory
grep: TMP.all.diff: No such file or directory
/usr/sbin/backup2l: line 660: TMP.all.obsolete: Permission denied
/usr/sbin/backup2l: line 661: TMP.all.new: Permission denied
grep: TMP.all.diff: No such file or directory
/usr/sbin/backup2l: line 667: TMP.all.new: No such file or directory
/usr/sbin/backup2l: line 667: TMP.all.files: Permission denied
/usr/sbin/backup2l: line 670: TMP.all.files: No such file or directory
grep: TMP.all.list: No such file or directory
grep: TMP.all.new: No such file or directory
grep: TMP.all.list: No such file or directory
grep: TMP.all.new: No such file or directory
grep: TMP.all.list: No such file or directory
  / 0 file(s), 0 / 0 dir(s), 0 B / 0 B (uncompressed)
grep: TMP.all.skipped: No such file or directory
grep: TMP.all.skipped: No such file or directory
grep: TMP.all.skipped: No such file or directory
  skipping: 0 file(s), 0 dir(s), 0 B (uncompressed)

Creating archive using 'DRIVER_TAR_GZ'...
  tar: TMP.all.files: Cannot stat: No such file or directory
  tar: Error is not recoverable: exiting now
  tar (child): TMP.all.tar.gz: Cannot open: Permission denied
  tar (child): Error is not recoverable: exiting now
Checking TOC of archive file (< real file, > archive entry)...
/usr/sbin/backup2l: line 761: TMP.all.toc: Permission denied
tar (child): TMP.all.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
/usr/sbin/backup2l: line 762: TMP.all.files: No such file or directory
tee: TMP.all.error: Permission denied
diff: TMP.all.toc: No such file or directory
gzip: TMP.all.list: No such file or directory
gzip: TMP.all.skipped: No such file or directory
gzip: TMP.all.obsolete: No such file or directory
gzip: TMP.all.error: No such file or directory
gzip: TMP.all.new: No such file or directory
mv: cannot stat 'TMP.all.skipped.gz': No such file or directory
mv: cannot stat 'TMP.all.new.gz': No such file or directory
mv: cannot stat 'TMP.all.obsolete.gz': No such file or directory
mv: cannot stat 'TMP.all.error.gz': No such file or directory
mv: cannot stat 'TMP.all.tar.gz': No such file or directory
mv: cannot stat 'TMP.all.list.gz': No such file or directory
Creating check file for <all.31>...
find: './lost+found': Permission denied
/usr/sbin/backup2l: line 460: TMP.all.check: Permission denied
mv: cannot stat 'TMP.all.check': No such file or directory

Running post-backup procedure...
  post-backup: nothing to do

Wed Dec 28 12:41:32 AEDT 2016


Summary
=======

Backup       Date       Time  |  Size   | Skipped  Files+D |  New  Obs. | Err.
------------------------------------------------------------------------------
all.1        2016-12-28 12:04 |   86.1M |       0       69 |   69     0 |    0
all.11       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.12       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.13       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.14       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.15       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.16       2016-12-28 12:04 |      1K |       0       69 |    0     0 |    0
all.2        2016-12-28 12:04 |   86.1M |       0       69 |   69     0 |    0
all.21       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.22       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.23       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.24       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.25       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.26       2016-12-28 12:05 |      1K |       0       69 |    0     0 |    0
all.3        2016-12-28 12:05 |   86.1M |       0       69 |   69     0 |    0

Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1       1.8T  326M  1.7T   1% /sharedfiles/backupdata


```

How do I set up the permissions so that this command can also be run from the script file?

The script file contents and permissions are as follows :-

Contents :-
```

#!/bin/bash
backup2l -b

```

Permissions :-
agarwaldvk@MyHomeServer:~$ ls -l ./backuptest.sh
-rwx------ 1 agarwaldvk agarwaldvk 227 Dec 28 13:48 ./backuptest.sh
agarwaldvk@MyHomeServer:~$


Best regards



Deepak

---

### Post by Graham_Willis on 2016-12-27
Show us the relevant crontab entry. As what user are you logged in when executing this command by hand and as what user is cron job executed?

---

### Post by agarwaldvk on 2016-12-28
Hi Graham_Willis


Thanks for your response.

I may inadvertently given the wrong information.

When I said that it ran OK when the command was issued at the terminal, I meant the physical command like so :-

backup2l -b

not as a cron job

My idea is to set up a cron job with a predefined frequency but the backup command would be run as a script file containing the command as shown above.

So, the intent is that I would have, in the script file, only 2 commands viz
1. the above command and
2. the mail command that would send out the email about the status of the backup job

The reason for me doing it this way is that the only way that I could get the system to send me an email at the completion of a cron job is to have a set up like so :-



And I was hoping that things would all fall into place following the same strategy, the only difference being the command in the script file but for some reason the backup command when run from the script file encounters the 'Permission Denied' stumbling block.

This was the script file and the cron job that worked perfectly :-

script file contents :-
```

#!/bin/bash
todaysdatetime=$(date)
mytext="the program has been run at :"
echo "$mytext $todaysdatetime" >> /home/agarwaldvk/testoutput.txt 2<&1
mail -s "Cron job status report" deepakagarwalathome@gmail.com < /home/agarwaldvk/testoutput.txt

```


Permissions :-
agarwaldvk@MyHomeServer:~$ ls -l ./test.sh
-rwx------ 1 agarwaldvk agarwaldvk 227 Dec 28 13:48 ./test.sh

In all cases, I am logged in as user 'agarwaldvk' where this user has sudo privileges.

Edit :-
I just tried it again now and it worked. I ran the script file and also the command at the terminal both with sudo privilege and it worked in both cases. I haven't set up the cron job yet for this one. I will do it once I know how to run the script with sudo privileges.

So, I believe the problem boils down to be able to run the script with sudo privileges - how do I do that? Can you please advise me on that?


Best regards


Deepak

---

