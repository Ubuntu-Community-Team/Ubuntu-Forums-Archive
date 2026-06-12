---
title: "Seeking help with backup script"
date: 2020-01-04
forum: Server Platforms
---

### Post by volkswagner on 2020-01-04
Greetings,

I'm not much of a script creator (more of a hacking reverse engineer doing R&D... "ripoff and duplicate").

I have a server with a proprietary ERP running. The ERP vendor created a daily backup
of the DB and important data and put's it into a TAR file. This file gets overwritten daily. 

My goal is to capture the file daily and save 7 days worth.

This script is what I've found from another author but modified by me.

The script will run on the ERP server for now.
I have an smb mount in /etc/fstab for the destination.

As you can see I'm using the cp command which has caused an issue (when file copy did not complete).
The cp process ended up as "uninterruptible" forcing me to do a hard reset on the server (it wouldn't cleanly
shutdown because file lock prevented unmounting of the source mount point. With the script as-is, I can't
ctrl+c to cause an interrupt. What command in the script will allow me to abort with ctrl+c?

My first question is what should I use instead of cp (rsync, scp, other)?
I wanted to keep the file name the same, and there are other files in the source directory that I don't want
to include in the backup (I know I can exclude those with rsync).

After I get the daily copy working, I think I'm going to be tasked with retaining one weekly for 52 weeks as well.

I'm not sure if I should use the source file and create a second task to run weekly. Either way I think I would
like the weekly archives to simply append the file name with yyyyMMdd type date (I'll need help with this).

If I use rysync should I remove the deletion of the old backup file before rysncing/copying the new backup (this line >> rm -Rf /mnt/ERP_bak/daily/$checkdate/*)
As of right now the TAR file is roughly 20Gig.

I would also like to have some sort of logging file place in the destination or elsewhere if that
makes more sense.


I'm not sure if the closing/exit commands at the end work or not, I have yet to get the script to complete, but
I was able to get the copy to start and copy roughly 25% into the proper destination. I believe the smb mount
became unavailable during the copy.


Here is the script... Thanks in advance!

```
date
clear
echo Initializing ...
checkdate=`date | awk '{print $1}'`

cd /mnt/ERP_bak/;

checkdir=`vdir ./ | grep "Recycle" | awk '{print $9}'`;
echo
echo "$checkdir";
echo

if [ "$checkdir" != "@Recycle" ]; then
echo "ERROR: The NAS SMB mount is not accessible at this time!"
echo "FATAL!"
exit 1
fi
cd /mnt/ERP_bak/daily

if [ `pwd` != /mnt/ERP_bak/daily ]; then
echo "ERROR: No directory for the TOC file!"
echo "FATAL!"
exit 1
fi
cd "/mnt/ERP_bak/daily/$checkdate"
if [ `pwd` != "/mnt/ERP_bak/daily/$checkdate" ]; then
echo "ERROR:  folder for today not found"
mkdir "/mnt/ERP_bak/daily/$checkdate"
echo "I created today's folder for you."
fi
rm -Rf /mnt/ERP_bak/daily/$checkdate/*
#############################################################################
# Main Section
#
#############################################################################
date
echo
case "$checkdate"
in

Mon)
echo "Commencing the Monday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;


Tue)
echo "Commencing the Tuesday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

Wed)
echo "Commencing the Wednesday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

Thu)
echo "Commencing the Thursday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

Fri)
echo "Commencing the Friday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

Sat)
echo "Commencing the Saturday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

Sun)
echo "Commencing the Sunday Backup"
cp /u/backups/ERPBACKUP.TAR ./
;;

*)
echo "FATAL ERROR: Unknown variable passed for day"
;;
esac

exit 0 ;
```

---

### Post by TheFu on 2020-01-04
Scripts that depend on the PWD are extremely fragile and often break.  Building a script that uses absolute paths is less likely to fail.

I'd use variables for the source and the target.  ```

SOURCE_BASE="/u/backups/ERPBACKUP.TAR"

BACKDIR=/mnt/ERP_bak/
```

As I copied the file, I'd insert the current date into the filename.  
```
/bin/cp SOURCE_FILE $BACKDIR/${DB_NAME}_$((date "+%F")).gz
```

Then I'd use a find command to clean up any of those tgz files older than X days.  Below is 20 days:
```
/usr/bin/find  $BACKDIR -type f -name $DB_NAME\* -atime 20 -delete
```

I'd verify the mount was there:
```
MNT-GOOD=`/bin/mount |grep  -c $BACKDIR `
if [[ "X0" = "X$MNT-GOOD"  ]] ; then
  echo "ERROR: Mount of $BACKDIR failed."
fi
```
I'm assuming bash.  Adding the "X" ensures that a failed mount-grep doesn't break things.

Notice how I use full paths to any commands. That is a best practice for scripting.  If someone changes the PATH by accident, best to have the exact version of a program running, not some alternate version due to an unexpected change.

If there isn't a trap, then <cntl>-c isn't blocked.  It just takes a really long time to copy 20G.  Is there a reason the tar file isn't compressed?  DBs usually compress 75% or more.

---

### Post by volkswagner on 2020-01-05
Thanks @TheFu

So you think cp command is the way to go?

I haven't unpacked the tar file, but it's more than a database. I believe it contains config files along w/ERP files which may contain images and drawings.

What if I were to use a compression utility to copy and compress to the destination? Could I do that in one command without using cp and keeping the original?

If I were to leave the .tar as is and use rsync, would rsync rewrite the entire file if it exists at destination or can it update/change only bits to make a new "current/accurate" copy?

---

### Post by kevdog on 2020-01-06
The problem you are trying to solve (backups) is a recurring topic throughout the years.  Perhaps looking at solutions many others have contributed to may be worth your time.  Veamm backup runs on linux -- I think its free, and borg backup with gui known as Vorta (also opensource free software), are two solutions you may want to take a look at.

---

### Post by TheFu on 2020-01-06
> **volkswagner said:**
> Thanks @TheFu

So you think cp command is the way to go?

I haven't unpacked the tar file, but it's more than a database. I believe it contains config files along w/ERP files which may contain images and drawings.

What if I were to use a compression utility to copy and compress to the destination? Could I do that in one command without using cp and keeping the original?

If I were to leave the .tar as is and use rsync, would rsync rewrite the entire file if it exists at destination or can it update/change only bits to make a new "current/accurate" copy?

I would do things completely differently.  First, I had have storage that supported LVM snapshots and create a snapshot of all the important areas before using a normal Unix backup tool like rdiff-backup.  I would "pull" the backups, not push and definitely not have them on the same system. "Pull" backups mitigated all sorts of attacks and other problems.

No way, no how, would I use tar.  tar is like ZIP for Unix, with the same limitations. No suitable for data over about 500MB in size. For anything larger, get a better tool.

rsync has issues with files over 2G.  Also, local files will just be copied since the algorithm thinks that is faster than trying to find and update blocks with differences. I used rsync for versioned backups about 10 yrs ago. Then the backups got larger and larger until each was taking over 45 min, then 60, then 90 minutes and I couldn't complete the backups in the allowed backup window.

No backup is actually a backup until the restore plan has worked onto new hardware.  

It would really, really, help to know which DBMS is used.

---

### Post by LHammonds on 2020-01-06
Since the ERP team setup the backup and it dumps to the same file every day, I would not mess with their procedure.

But to increase the number of backups you can restore from, I would setup the remote backup repository to connect to that ERP server and copy that daily backup file to the repository.

And since you want to keep the filenames the same, that means using different target folders.

I would first have the repository copy the file to a temporary location such as /backup/erp/filename.tar.  Then check if today is a special day such as the 1st of the month, 1st of the quarter or 1st of the year and copy the file in the temporary folder (which is a local copy at this point) to one or more of those special folders.

I would then move the file from the temporary location to the final destination (one of they weekday folders) and overwrite whatever is there.

Example file/folder structure on repository:

/backup/erp/yearly/filename.tar
/backup/erp/monthly/filename.tar
/backup/erp/quarterly/filename.tar
/backup/erp/sunday/filename.tar
/backup/erp/monday/filename.tar
/backup/erp/tuesday/filename.tar
/backup/erp/wednesday/filename.tar
/backup/erp/thursday/filename.tar
/backup/erp/friday/filename.tar
/backup/erp/saturday/filename.tar

This would ensure you have 7 days worth of backups and 0 to 3 extended backups (0 extra if January 1st because you will have 4 copies of that day).  It also makes sure the backup file travels over the wire only one time each day in case that step takes a long time.

LHammonds

---

### Post by volkswagner on 2020-01-09
Thanks for all of the suggestions.

I don't need to keep the file name the same, I just thought that
would be best to do an automatic overwrite without the need to 
clean up the daily files.

I still need to do some testing.
I'll post back once I have more questions
or a working setup.

Cheers!

---

### Post by TheFu on 2020-01-09
> **volkswagner said:**
> Thanks for all of the suggestions.

I don't need to keep the file name the same, I just thought that
would be best to do an automatic overwrite without the need to 
clean up the daily files.

I still need to do some testing.
I'll post back once I have more questions
or a working setup.

Cheers!

If you learn of an issue on the 6th day after it happened and need to restore, during the restore, the file you are trying to restore could be overwritten by a new backup if the filenames are the same.  I've had that happen back before I switched.  I've had lots of problems over the decades with backups, which is why I do certain things specific ways.  An ounce of prevention....

---

