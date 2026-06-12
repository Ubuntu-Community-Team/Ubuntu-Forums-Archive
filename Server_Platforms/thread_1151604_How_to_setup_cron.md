---
title: "How to setup cron?"
date: 2009-05-07
forum: Server Platforms
---

### Post by Jarn on 2009-05-07
Hi, I made a simple script that I want to run every week to back up some files (it just runs the back up and then cps it to an external drive). I know the script works because when I run it manually everything is fine. However, I can't figure out how to get it to run every week. I created a symlink in /etc/cron.weekly to the script in question, but it never runs. Is there something else I need to do?

---

### Post by bluefrog on 2009-05-07
you could add it with crontab -e to see if it works this way.

---

### Post by Jarn on 2009-05-11
Okay, thanks. I can get cron to run the script now. However, it doesn't work when it is run by cron but it works fine when it's run manually? The contents of the script are this:

```
echo -e "Backing up the webpage...\n"
/usr/bin/curl -b /tmp/cookies.txt -c /tmp/cookies.txt -L --max-redirs 1000 -v "(there's a website address here that downloads a file to /home/chair/backups/file.zip)"
echo -e "Copying backup to /home/chair/backups...\n"
/bin/cp /home/chair/backups/file.zip /home/chair/backups/file-`date '+%Y%m%d'`.zip
echo -e "Copying backup to /data/backups on second hard drive...\n"
/bin/mv /home/chair/backups/file.zip /data/backups/file-`date '+%Y%m%d'`.zip

```

What happens when cron runs it is simply nothing. The result is a 0 byte file.zip. I call the command in cron with /home/chair/bin/weekly_bak. When I have cron call it with /home/chair/bin/weekly_bak &> /home/chair/test.txt to see what the output is, test.txt is created but it's blank.

---

### Post by Alekz_ on 2009-05-11
Hi Jarn!

You should read tha crontab man

```
man crontab
```

It'll help you!

The crontab -e command opens you a file to add content for the schedule, not the script it self!

It seems like:
```
0 22 * * * /scripts/your_script.sh
```

Where:
0 = minute
22 = hour
* = day of the month (* means everyday)
* = month (* means every month)
* = weekday (* means everyday)
/scripts/your_script.sh = the script

Hope it helps!

---

### Post by Jarn on 2009-05-11
Alekz, you misunderstand me - that's what I did. I have cron set to run /home/chair/bin/weekly_bak with the line:
```

0 0 * * 1 /home/chair/bin/weekly_bak

```
However, the script executes as intended at midnight on Monday but it doesn't do what it's supposed to. Where it's supposed to download a file, then copy it to some place what happens is that a 0kb file is produced and no copy takes place. It works fine when I run it manually, though. What I posted was the contents of the script - I was hoping someone could give me some insight into why it doesn't work when cron tries to run it automatically but works fine when I run it myself, if there's something in the script that cron doesn't like or if it's a permissions issue or what.

---

### Post by Alekz_ on 2009-05-11
Sorry! I missunderstood! :(

Well, I may sugest you to put this line in front of your script in crontab:

```
0 0 * * 1 /home/chair/bin/weekly_bak 2> /tmp/bkp.log
```

It should output any error message to /tmp/bkp.log

Ah! Another thing... The user you make the cron schedule have the permission to access data you wanna backup, and, of course, execute the commands which your script run? (stupid question, but it happens some times...)

---

### Post by Jarn on 2009-05-11
Yeah, the user who scheduled the script has access to run the script. I didn't use sudo when calling either crontab or the script when I run it manually which, unless there's something I don't know about cron, should mean that it's running as the same user both times...

Doesn't &> pick up 2> also? I tried doing that already, piping the output to a log in crontab - the logfile was blank.

---

### Post by Alekz_ on 2009-05-12
Well.. I don't know what else it could be..

I'm gonna do a stupid question.. Is your crond runnig?!

Do a test with a different task.. kind of:

```
0 15 * * * touch /tmp/cron_test
```

Just to see if it's working...

---

### Post by Jarn on 2009-05-12
cron_test is created at the specified time...

---

### Post by Alekz_ on 2009-05-12
Ha! At least we know your cron works! :)

Look, I made some changes on your script

```
#!/bin/bash

log_file="/tmp/web_bkp.log"

echo "Script started on `date '+%m/%d/%y'` at `date '+%H:%M:%S'`" > $log_file

echo "-----------------------------------------------------------------------------" >> $log_file

echo "Backing up the webpage..." >> $log_file
/usr/bin/curl -b /tmp/cookies.txt -c /tmp/cookies.txt -L --max-redirs 1000 -v

if [ $? -eq 0 ]; then
	echo "Backup complete!" >> $log_file
else
	echo "Backup fails!" >> $log_file
fi

echo "Copying backup to /home/chair/backups..." >> $log_file
/bin/cp /home/chair/backups/file.zip /home/chair/backups/file-`date '+%Y%m%d'`.zip

if [ $? -eq 0 ]; then
	echo "Status: ok!" >> $log_file
else
	echo "Status: Fail!" >> $log_file
fi

echo "Copying backup to /data/backups on second hard drive..." >> $log_file
/bin/mv /home/chair/backups/file.zip /data/backups/file-`date '+%Y%m%d'`.zip

if [ $? -eq 0 ]; then
	echo "Status: ok!" >> $log_file
else
	echo "Status: Fail!" >> $log_file
fi
```

Try to schedule this script and we'll see if it create some log! It HAVE to!

---

### Post by Jarn on 2009-05-12
Here's the contents of the log file when I set cron up to run the script:

```

Script started on 05/12/09 at 15:33:01
-----------------------------------------------------------------------------
Backing up the webpage...
Backup fails!
Copying backup to /home/chair/backups...
Status: Fail!
Copying backup to /data/backups on second hard drive...
Status: Fail!

```

Here's the contents when I run the script manually:

```

Script started on 05/12/09 at 15:37:04
-----------------------------------------------------------------------------
Backing up the webpage...
Backup complete!
Copying backup to /home/chair/backups...
Status: ok!
Copying backup to /data/backups on second hard drive...
Status: ok!

```

---

### Post by Alekz_ on 2009-05-12
Man.. I'm out of suggestions! :(

It looks to be a permission issue, but you already told me that you're executing and scheduling the script with the same user!

The problem is that these commands don't have an error code table (only 0 for success and 1 for error!), so it's kind of hard to debug...

Well, I don't know if it's against the forum rulles, but you could consider to schedule the script with root account.. IF it's a permission problem, it won't show any error message!

I don't know!

Any ideas are welcome! :)

---

### Post by Jarn on 2009-05-12
Running the script with sudo produces no errors. Putting it in sudo crontab -e and letting cron run it produces this in the log:

```

Script started on 05/12/09 at 17:19:01
-----------------------------------------------------------------------------
Backing up the webpage...
Backup fails!
Copying backup to /data/backups on second hard drive...
Status: ok!
Copying backup to /home/chair/backups...
Status: ok!

```

What happened was the backup created a 0kb file with the correct name but produced an error and then propagating that backup to the two locations both succeeded because they just moved the 0 kb file... now I'm really confused.

---

### Post by Alekz_ on 2009-05-13
Hi Jarn!

I don't know how the `curl` command works (or what it do), but if it isn't running as root, something is wrong!

Do some tests running the command with 'sudo' and see with is there any error messages...

---

### Post by Jarn on 2009-05-13
The script runs fine when running as root via sudo (i.e. "sudo <path to script>" performs the backup fine). It doesn't run fine when run as root via cron (i.e. putting <path to script> in "sudo crontab -e" produces the output listed above).

---

