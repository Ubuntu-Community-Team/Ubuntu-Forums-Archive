---
title: "Problem with cron job"
date: 2015-06-06
forum: Server Platforms
---

### Post by ndnd on 2015-06-06
Hello,
I am trying to include as much information as possible because I am not able to figure out why the cron.job is not running. 
I made two files for running on cron.hourly.  When I run the > run-parts -v /etc/cron.hourly they both run fine.  I want to move this to cron.monthly and have only put the files in cron.hourly for testing. I am including file permissions information below

> 
-rwxr-xr-x 1 root root 1330 Jun  5 03:20 data_backup
-rwxr-xr-x 1 root root  948 Jun  5 03:43 systembk



The script from both files is below. Now there is a customized command for 'gcloud' which is google's cloud however, I think the problem is related to script and nothing to to do with that specific command. 

data_backupfile
> 
#!/bin/bash
# Date: June 3 2015
# 
# Goal is to backup the data disk (take snapshot)
# Following the guidelines in documentation mentioned below
##########################################################
#
# Comments
# Comments
#
#Comments
#
##########################################################


PATH=/sbin:/bin:/usr/bin:/usr/bin/gcloud

echo $PATH

#sudo pkill -u user1
#sudo pkill -u user2
###sudo sync
###sudo fsfreeze -f /home/user1/Desktop/data
# Alternative to the above two commands of sync and fsfreeze
# Umount all the attachd drives (except the boot disk)
sudo umount -a
echo umount
data1=databackup-1-$(date +"%Y-%m-%d-%H-%M")
data2=databackup-2-$(date +"%Y-%m-%d-%H-%M")
echo $data1
#gcloud compute disks snapshot disk-3 disk-4 \
#--zone us-central1-b
##--snapshot-names databackup-1 databackup-2 --zone us-central1-b
gcloud compute disks snapshot disk-3 disk-4 \
--snapshot-names $data1 $data2  --zone us-central1-b
###sudo fsfreeze -u /home/user1/Desktop/data
#Alternative to Fsfreeze
sudo mount -a



The second file is for taking backup of the system disk and I believe I am doing something wrong (maybe owner has to be the user not the root or is there something related to crontab. 

I think I am missing a some basic step here. 

> 
#!/bin/bash
# Date: June 3 2015
# 
# Goal is to backup the system disk (take snapshot)
# Following the guidelines in documentation mentioned below
##########################################################
#
# Comment 1 
# Comment 2
#
#
##########################################################
# This is system disk so  will have to take a live snapshot

PATH=/sbin:/bin:/usr/bin:/usr/bin/gcloud

# Flush data from buffers
sudo sync
sysdata1=sysdatabackup-1-$(date +"%Y-%m-%d-%H-%M")
gcloud compute disks snapshot analyze-2 \
--snapshot-names $sysdata1 --zone us-central1-b



My thoughts 

1) Make an executable script and move it to /etc/cron.hourly/ folder 
2) Now test is with $run-parts -v /etc/cron.hourly/ 
3) If tests runs ok. your script should work ? (That is my assumption)

Thanks in advance for your help

---

### Post by ian-weisser on 2015-06-07
Here's what I see:

You running run-parts as a user is different from cron running run-parts as root. The permissions and environment will be different...a great first test for many common syntax errors, but not a great final test for functionality.

Tasks in /etc/cron.* already run as root. Do not use sudo in them unless you intend to run them as a *different non-root user.*

'echo' commands don't work in cron - no console assigned; cron runs headless. Best practice is to redirect the output to a logfile or temporary debugging file (echo $output > /tmp/cron_debug_file)

---

### Post by ndnd on 2015-06-07
Thanks ian-weisser,
Where should I put the $echo $output>/tmp/cron_debug_file line (at the end of the script or somewhere in between).

---

### Post by ian-weisser on 2015-06-07
> **ndnd said:**
> Where should I put the $echo $output>/tmp/cron_debug_file line (at the end of the script or somewhere in between).

It's merely an example of how to adapt your existing 'echo' lines, which we all use for convenient debugging and testing, to headless (non-console) operation. '$output' could be '$data1' or any test you think will help you figure out what's going on.

The only reason I mentioned it is because...as you have already discovered...cron will happily fail silently, and won't tell you why unless you redirect output.

Another trick to debugging cron jobs is to redirect error output to a logfile. That's what all those cryptic '/path/to/logfile 2>&1' instructions do at the end of cronjob lines - they redirect output and errors to wherever you want them. Then you'll know *exactly* why the system didn't like a cronjob.

---

### Post by SeijiSensei on 2015-06-07
One simple solution is to call those scripts from another "wrapper" script like this:
```

#!/bin/sh

LOG=/var/log/myscript.log

# run these scripts every month and write their output to a log file
/path/to/data_backup >> $LOG 2>&1
/path/to/systembk >> $LOG 2>&1


```
Then put this script in cron.monthly instead. That will invoke each of your scripts and direct their output to /var/log/myscript.log.  (You could use separate log files instead, of course.) The mysterious "2>&1" parameter tells the shell to send any output for "stderr," the error device ("2"), to "stdout" ("1") instead.  Then all the output from the scripts will be logged in one file.

Usually I keep all the scripts I write for system management in the /usr/local/sbin/ directory.  Then I use a symbolic link in the cron.* directories like this:
```

cd /etc/cron.monthly
sudo ln -s /usr/local/sbin/myscript

```

---

### Post by LHammonds on 2015-06-09
When writing scripts that will be automated, I consider 3 modes of output.

Mode 1 - Unexpected output to be captured and redirected from the automated scheduler
Mode 2 - Output you want someone to see if they are manually running the job
Mode 3 - Output you want saved in a log

Its typical to just have mode 3 output by declaring a variable pointing to your scripts' log file and re-directing any output you want saved to that log.

Example:
```

LOGFILE="/var/log/myscript.log"
echo "Backup started." >> ${LOGFILE}
rsync -apogHK --delete --exclude=*.pid ${APPDIR} ${TARGET} 1>/dev/null 2>&1
echo "Backup completed." >> ${LOGFILE}

```

For mode 2 logging, if you expect this script to have a dual purpose of being run manually and via crontab, you can modify your output a bit to show certain events to the console as well as logging them.  The below example will send output to both the standard out (screen) and a log file.  This way, if the person didn't even care about the output or missed it by getting a cup of coffee, they can review the logs and see everything they missed.

Example:
```

LOGFILE="/var/log/myscript.log"
echo "Backup started." | tee -a ${LOGFILE}
rsync -apogHK --delete --exclude=*.pid ${APPDIR} ${TARGET} 1>/dev/null 2>&1
echo "Backup completed." | tee -a ${LOGFILE}

```

For mode 1 logging, you can use either mode 2 or 3 inside the script and simply re-direct the output of the script to another log in addition to the script log or effectively block it.

Crontab Example (ignoring any standard or error output from the script)
```

10 1 * * * /var/scripts/myscript.sh > /dev/null 2>&1

```

Crontab Example (saving any output to a log file)
```

10 1 * * * /var/scripts/myscript.sh >> /var/log/myscript.cron.log 2>&1

```

Keep in mind that if you save additional log info at the schedule level, it might double the entries if you are using mode 2 which sends info to the screen for people manually running it.

My jobs are typically just mode 3 with all crontab output being sent to null device.  I have some jobs I run manually and I use the "tee" option to output status info to the screen for long-running jobs.  If I need to debug issues, I typically modify my script to output more details.  Some programs like rsync will send a TON of data to a log file so just be careful what you record.  I like keeping my log files as small as possible so I can keep data about the jobs longer as well as make it easy to review prior executions.

NOTE that a single ">" symbol will create a new file or overwrite an existing file.  A double ">>" symbol will create a new file or append to the bottom of an existing one.

LHammonds

---

