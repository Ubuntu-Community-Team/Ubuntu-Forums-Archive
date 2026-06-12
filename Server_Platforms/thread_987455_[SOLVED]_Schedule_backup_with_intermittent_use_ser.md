---
title: "[SOLVED] Schedule backup with intermittent use server"
date: 2008-11-19
forum: Server Platforms
---

### Post by cmittle on 2008-11-19
I have written a backup script that uses rsync to backup my server to another internal disc.  I would like to schedule this to run automatically, but the biggest problem I'm seeing is that I don't run my server 24/7.  I turn it on periodically, recently I've been turning it on on weekday mornings b/c I'm not doing anything at work and can work on my personal stuff, and sometimes on the weekends for access to music files and documents.  

I know that fsck runs based on the number of times the computer has been turned on, is there a way to relate a script to that?  Does anyone have a suggestion?

thanks,
cory

---

### Post by cdenley on 2008-11-19
What do you mean? Back it up based on the number of times the server has been rebooted? Based on the time since the last backup? Maybe back it up daily, and at boot if it hasn't been done in a few days?

---

### Post by MJN on 2008-11-19
You might be interested in [Anacron]("http://anacron.sourceforge.net/"). Like Cron it is a command scheduler but its forte lies in its ability to accommodate the situation where machines don't run 24/7 and hence would otherwise potentially miss out on scheduled tasks. It does this by approaching scheduling from a different perspective, specifically executing tasks based on the length of time since they were last performed.

Note that if interupted, rsync will quite happily continue from where it left off next time it is run however you will need to make sure that your controlling script is as well. Specifically, it needs to be able to cope with the potential for you  (presumably) turning the machine off on a whim without necessarily checking to see if a backup is currently underway. If it is a basic script that does nothing but call rsync with various parameters then this is unlikely to be a problem, however if it performs elaborate logging or archive manipulation etc then you may need to give it some thought.

Mathew

---

### Post by cmittle on 2008-12-01
Thanks for the help MJN.  I've set it up in Anacron to run every 15 days.  It is a very simple script (my first) that I've put together with the help of some tutorials and man page digging, so I think it will be fine.  Is there a good way to tell if/when the script ran last?

Thanks,
Cory

---

### Post by MJN on 2008-12-01
Ordinarily a backup script would ideally include some form of timestamping within the backup however in your case you don't really know if your backups will be completing before the machine is turned off.

I would recommend making your script log its actions to a file. Specifically, it should indicate when it started and when it stopped - you will then be able to see when it ran and if/when it completed.

Something like the following would suffice:

```
echo -e "\nBackup started `date`" >> backupscript.log

# Your backup commands here

echo -e "Backup finished `date`" >> backupscript.log
```

Mathew

---

### Post by cmittle on 2008-12-01
I've added the command you suggested around the backup commands in my script, but I'm not having any luck getting it to work.  Here is my script now.

```
#!/bin/sh
progname=${0##*/}
toppid=$$
#above used to grab the name of the script and associated
#process id

Util="/usr/bin/rsync"

#Folders to exclude
EXCLUDES=/media/160gdisk/rsync/text/exclude.txt
#Folders to include
INCLUDES=/media/160gdisk/rsync/text/include.txt


##Define backup path
PATH=/media/160gdisk/rsync/backup

#####Rsync options to be used
#-n dry run
#-a archive; tells rsync to retain permissions and ownership and recursive
#-v verbose
#-z compress
#--progress tells user how many files are left to be copied
#--delete any files on the receiving side if they do not exist
	#on the sending side
#-t transfers modification timestamp with files
#--include-from=FILE points to include file; this is read as exception to excludes..maybe
#--exclude-from=FILE points to exclude file

OPTS="-azt --progress --delete --include-from=$INCLUDES --exclude-from=$EXCLUDES "

#Display statement
echo "Preparing to backup with..."

#Echo command that will run
echo $Util $OPTS / $PATH
echo $progname

echo -e "\nBackup started 'date'" >> /media/160gdisk/rsync/text/server_backup.log

#Run actual command
echo "Process ID = "$toppid
$Util $OPTS / $PATH

echo -e "Backup complete 'date'" >> /media/160gdisk/rsync/text/server_backup.log


```

This is what I get in my log file.
```
-e 
Backup started 'date'
-e Backup complete 'date'

```

I've tried playing with the syntax a little bit but this is my first script writing experience and I've had little luck with that.  If you could tell me what I'm doing wrong that would be great.

Thanks,
Cory

---

### Post by MJN on 2008-12-01
Ah, that's probably a result of Ubuntu moving from Bash to Dash as its default shell interpreter.

In this instance just drop the **-e** flags and the **\n** in the echo statements.

Alternatively, change the beginning of your script to read **#!/bin/bash**

Mathew

---

### Post by hictio on 2008-12-01
```

echo -e "Backup complete 'date'

```

It seems to me that you are using the wrong type of single qoutes, try these ones
```

`date`

```
On an keyboard with English layout, those should be above the Tab key.

One other thing, once the script is running, be sure to rotate the file '/media/160gdisk/rsync/text/server_backup.log', since you are appending the output on each exceution, the file will just keep on growing, take a look a logrotate.conf, or add something like this to it:
```

/media/160gdisk/rsync/text/server_backup.log {
        weekly
        rotate 4
        notifempty
        copytruncate
}

```

This will rotate the file weekly, and keep a month of backlogs.

---

### Post by MJN on 2008-12-01
Well spotted hictio with the quots.

The -e flash will certainly cause a problem as it seems to be a 'BASHism'.

Mathew

---

### Post by hictio on 2008-12-01
> **hictio said:**
> 
One other thing, once the script is running, be sure to rotate the file '/media/160gdisk/rsync/text/server_backup.log', since you are appending the output on each exceution, the file will just keep on growing, take a look a logrotate.conf, or add something like this to it:
```

/media/160gdisk/rsync/text/server_backup.log {
        weekly
        rotate 4
        notifempty
        copytruncate
}

```

This will rotate the file weekly, and keep a month of backlogs.

Another thing you can do, if you don't want to deal with rotation, is making the first instance of the log redirection to use a single '>', like this:

```

echo -e "\nBackup started `date`" > backupscript.log

```

The other one remains the same, this will make the first instance to rewrite the old file with a new instance upon execution, it won't grow.

---

### Post by MJN on 2008-12-01
I purposely used >> as in this instance it is important to maintain a full history of backup 'attempts' in order to show when the last backup was run in its entirety.

To be honest I wouldn't ever bother rotating it - there's really no need as the size of the file is never going to be worth worrying about. At, say, 50bytes/day (assuming a backup is run every day) then it'll grow to 18KB in a year!

Mathew

---

### Post by hictio on 2008-12-01
I understand it, but I can't control myself, it's an old habit from days with smaller HDDs :D

---

### Post by MJN on 2008-12-02
There are worse habits I'm sure! :-)
 
Mathew

---

### Post by cmittle on 2008-12-02
I've change it to /bin/bash at the top, and also changed my ' to ` , but it still doesn't work.  I get the following output;

```

/path/to/script.sh: 39 date: command not found

Rsync stuff working...

/path/to/script.sh: 45 date: command not found
```

I've tried this;

```
echo -e "Backup Started `date`"
```

and this
```
 echo "Backup Started " `date` 
```
and this

```
 echo -e "Backup Started " `date` 
```

Still no luck...  I'm trying to learn more about this but the syntax is a little tricky


I managed to make one thing kind of work.  I added this to the top of my script;
```
 START_TIME=$(date)
```

and modified the following;
```
 echo -e "\nBackup started "$START_DATE >> /path/to/logfile.log
```

This worked, but now I don't know how to show a start time and end time for the process.  Any ideas?

cory

---

### Post by MJN on 2008-12-02
What happens if you type **date** at the command line?

Edit: Aha - spotted the problem!

> ```
##Define backup path
PATH=/media/160gdisk/rsync/backup
```$PATH is already a system variable - and a key one at that as it declares the valid search areas to find files. By overwriting the default $PATH you have inadvertently made the script unable to find the 'date' command (which resides in /bin/ but it has no way of knowing that).

Change your variable e.g. BACKUPPATH=/media/160gdisk/rsync/backup and modify and references to it.

Mathew

---

### Post by cmittle on 2008-12-03
Good eye.  Thanks so much for the help.  I guess that's what I get for trying to copy other peoples scripts and modifying them.  

I would like to learn a little bit more about bash, do you have any particular source of information you suggest I read?  


Cory

---

