---
title: "Differential/Incremental Backups Linux to Windows"
date: 2011-01-25
forum: Server Platforms
---

### Post by Fooshnik on 2011-01-25
I'm wondering if anyone has worked out a way to perform a differential backup from their linux server to windows. I have a mix of windows/ubuntu and everything is working except ext3 doesn't support using the archive bit so my linux servers are backing up everything every night. I'd like to save the backup space (and time) by using differentials but have yet to discover an effective way to do so. If anyone has this set up please post how you did it.

---

### Post by John Raycheba on 2011-01-27
Hi,
 
I have a script that's been working for a few months.
 
As currently set up the script does the following:
 
1. A full backup on the 1st Sunday of the month.
2. A differential back every day after that, BUT,
3. The daily differential backups are overwritten, EXCEPT, for the Sunday.
 
The script is easily changed to alter the timing of the full and differential backups OR to have it do daily incremental backups.
 
Note: The script is NOT perfect as it generates one error message indicating that a file is not found. I believe this may be when it is trying to erase a temporary file. in any case it does work.
 
The three files listed below should all be placed in the same directory and script "backup_filesystem.sh" should be run by the root user.
 
Also, the "backup_files_include.txt" file can, and is empty because the script assumes that everything will be backed up.
 
The "backup_files_exclude.txt" file cantains the list of directories and files that should NOT be backed up. In the example file you will note that the mySQL databases are not backed up because there are beter ways of doing that.
 
 
**backup_filesystem.sh**
```
#!/bin/bash
####################################
#
# Backup to NFS mount script with
# grandfather-father-son rotation.
#
# from Ubuntu 10.04 server manual modified by JR
# Last update: 2010-11-15
#
# The purpose of this script is to provide full, monthly filesystem backups for one year
# before they are overwritten.
# The weekly and daily backups are "differential"; that is,
# the system can be restored to a given month, *week of the most recent month* 
# and *day of the most recent week*
# by restoring at most two backup files.
#
# A weekly full backup can be achieved by uncommenting four lines of code.
#
# It is assumed that this script and the two files defined by BACKUP_FILES_INCLUDE and BACKUP_FILES_EXCLUDE are
# in the same directory and that this is the current working directory when it is executed.
#
# The "cron job" that runs this script should first change to the directory that contains this script
# before running it.
#
# Notes: 
# 1. It is important to run this script at a time of day when there is a minimum of other activity, 
#    expecially when full backups are being done.
#
# 2. As currently configured, the full backups are done on the first Sunday of the month (or week).
#    The day of the week on which the full backups are done can be changed by editing the value of
#    the FULLBACKUPWEEKDAY_NUM variable. 
#
####################################
HOSTNAME=$(hostname -s)
BACKUP_FILES="/"      #Assume that ALL files are to be backed up.
BACKUP_FILES_INCLUDE="backup_files_include.txt"  #This file is empty.
BACKUP_FILES_EXCLUDE="backup_files_exclude.txt"  #Exclude files that should not be backed up. E.g., databases, which will be backed up by a separate procedure.
# Backup directory(where to save the backup files).
BACKUP_DIR="/mnt/sdb1/backups"
LOGFILE="$HOSTNAME-backup.log"
SNAPSHOT_FILE="$HOSTNAME-backup_snapshot"
SNAPSHOT_FILE_SAVED="$HOSTNAME-backup_snapshot_saved"
IS_DAILY=0
IS_WEEKLY=0
IS_MONTHLY=0
IS_FIRSTRUN=0   # <> 0 if IS first run
FULLBACKUPWEEKDAY_NUM=0 #Do full backups on Sunday (weekday_num = 0)
# Setup variables for use in constructing archive filenames.
YEAR_NUM=$(date +%Y)
MONTH_NUM=$(date +%m)
WEEKOFYEAR_NUM=$(date +%U)  # 00 to 53 with Sunday as start of week
DAYOFYEAR_NUM=$(date +%j)   # 001 to 366 Julian day of year
DAYOFMONTH_NUM=$(date +%d)  # 01 TO 31
DAYOFWEEK=$(date +%A)       # as a word; e.g., Sunday
#echo $DAYOFWEEK
DAYOFWEEK_NUM=$(date +%w)   # 0 to 6; i.e., Sunday to Saturday
#WEEKOFMONTH_NUM=$(( (WEEKOFYEAR_NUM + 1) / MONTH_NUM ))  # 1 to 5
if [ $DAYOFMONTH_NUM <= 6 ]; then
  WEEKOFMONTH_NUM=1
  elif (( $DAYOFMONTH_NUM > 6  &&  $DAYOFMONTH_NUM <= 13 )); then
    WEEKOFMONTH_NUM=2
    elif (( $DAYOFMONTH_NUM > 13  &&  $DAYOFMONTH_NUM <= 20 )); then
      WEEKOFMONTH_NUM=3
      elif (( $DAYOFMONTH_NUM > 20  &&  $DAYOFMONTH_NUM <= 27 )); then
        WEEKOFMONTH_NUM=4
        elif ( $DAYOFMONTH_NUM > 27 ) ; then
          WEEKOFMONTH_NUM=5
fi
#Is today the the first Sunday (fullbackupday_num) of the month.
if (( ($DAYOFWEEK_NUM == $FULLBACKUPWEEKDAY_NUM)  &&  ($DAYOFMONTH_NUM < 7) )); then 
  IS_MONTHLY=1                                                  #1st Sunday of the month
  elif [ $DAYOFWEEK_NUM == $FULLBACKUPWEEKDAY_NUM ]; then
    IS_WEEKLY=1                                                 #Sunday, but not the 1st of the month
    else
      IS_DAILY=1                                                #not a Sunday
fi
#If snapshot file doesn't exist then do set  firstrun to 1 and do a full backup.
if [ -f $BACKUP_DIR/$SNAPSHOT_FILE ]; then 
  IS_FIRSTRUN=0
  else IS_FIRSTRUN=1
fi
#echo "year is: $YEAR_NUM"
#echo "month is: $MONTH_NUM"
#echo "week of year is: $WEEKOFYEAR_NUM"
#echo "day of year is: $DAYOFYEAR_NUM"
#echo "week of month is: $WEEKOFMONTH_NUM"
#echo "day of month is: $DAYOFMONTH_NUM"
#echo "day of week is: $DAYOFWEEK_NUM"
#echo "is_monthly: $IS_MONTHLY"
#echo "is_weekly: $IS_WEEKLY"
#echo "is_daily: $IS_DAILY"
#echo "is_firstrun: $IS_FIRSTRUN"
#exit #uncomment for testing
#Create Archive file name
if [ $IS_MONTHLY == 1 ] ; then
#if [ $IS_MONTHLY == 1 ] || [ $IS_FIRSTRUN != 0 ] ; then
  ARCHIVE_FILE="$HOSTNAME-month-$MONTH_NUM.tgz"
  elif [ $IS_FIRSTRUN == 1 ] ; then
    ARCHIVE_FILE="$HOSTNAME-month-$MONTH_NUM.tgz"
    elif [ $IS_WEEKLY == 1 ]; then
      ARCHIVE_FILE="$HOSTNAME-week-$WEEKOFMONTH_NUM.tgz"
      #ARCHIVE_FILE="$HOSTNAME-month-$MONTH_NUM-week-$WEEKOFMONTH_NUM.tgz" #uncomment if weekly is to be a full backup
      elif [ $IS_DAILY == 1 ] ; then
        ARCHIVE_FILE="$HOSTNAME-weekday-$DAYOFWEEK_NUM.tgz"
fi
#echo "Archive name is $ARCHIVE_FILE"
#exit #uncomment for testing
# Print start status message to log file.
echo >> $BACKUP_DIR/$LOGFILE
date >> $BACKUP_DIR/$LOGFILE
echo "Backing up $BACKUP_FILES to $BACKUP_DIR/$ARCHIVE_FILE" >> $BACKUP_DIR/$LOGFILE
# Do full or differential backup
# If SNAPSHOT_FILE does not exist, a full backup is done
# If SNAPSHOT_FILE does exist then save it to SNAPSHOT_FILE_SAVED
# Do the (incremental / differential) backup
# Copy SNAPSHOT_FILE_SAVED over SNAPSHOT_FILE so that the next backup will include changes from the last
# full backup rather than the last (incremental) backup.
# When a full backup is wanted, erase both SNAPSHOT_FILE and SNAPSHOT_FILE_SAVED
# Do the erase for the monthly backup, which will be the full backup while the weekly and daily backups
# will be the incremental / differential from the last monthly backup.
#if [ $IS_MONTHLY == 1 ] ; then
if [ $IS_MONTHLY == 1 ] || [ $IS_FIRSTRUN != 0 ] ; then
  #echo "1. deleting  $BACKUP_DIR/$SNAPSHOT_FILE" 
  rm -f $BACKUP_DIR/$SNAPSHOT_FILE                      #delete snapshot so a full backup will be done
  rm -f $BACKUP_DIR/$SNAPSHOT_FILE_SAVED
#  elif [ $IS_FIRSTRUN != 0 ] ; then
#    #echo "2. deleting  $BACKUP_DIR/$SNAPSHOT_FILE" 
#    rm -f $BACKUP_DIR/$SNAPSHOT_FILE                    #delete snapshot so a full backup will be done
#    rm -f $BACKUP_DIR/$SNAPSHOT_FILE_SAVED
#   elif [ $IS_WEEKLY == 1 ] ; then                     #uncomment if weekly is to be a full backup
#     rm -f $BACKUP_DIR/$SNAPSHOT_FILE                  #uncomment if weekly is to be a full backup
#     rm -f $BACKUP_DIR/$SNAPSHOT_FILE_SAVED            #uncomment if weekly is to be a full backup
fi
#if snapshot exists save it
if [ -f $BACKUP_DIR/$SNAPSHOT_FILE ]; then 
  #echo "3. Saving $BACKUP_DIR/$SNAPSHOT_FILE to $BACKUP_DIR/$SNAPSHOT_FILE_SAVED"
  cp -p $BACKUP_DIR/$SNAPSHOT_FILE $BACKUP_DIR/$SNAPSHOT_FILE_SAVED >> $BACKUP_DIR/$LOGFILE 2>&1
fi
tar -czf $BACKUP_DIR/$ARCHIVE_FILE $BACKUP_FILES \
    --files-from=$BACKUP_FILES_INCLUDE \
    --exclude-caches \
    --exclude-from=$BACKUP_FILES_EXCLUDE \
    --no-check-device \
    --listed-incremental=$BACKUP_DIR/$SNAPSHOT_FILE \
    >> $BACKUP_DIR/$LOGFILE 2>&1                            #stderr and stdout to logfile
    #2>> $BACKUP_DIR/$LOGFILE \                             #stderr to logfile
    #1> /dev/null                                           #stdout to null
#If not a full backup, saved snapshot file exists, restore it so differential rather than incremental backups can be made
if [ -f $BACKUP_DIR/$SNAPSHOT_FILE_SAVED ]
  then
    rm -f $BACKUP_DIR/$SNAPSHOT_FILE >> $BACKUP_DIR/$LOGFILE 2>&1
    #echo "4. Restoring $BACKUP_DIR/$SNAPSHOT_FILE_SAVED $BACKUP_DIR/$SNAPSHOT_FILE"
    cp -p $BACKUP_DIR/$SNAPSHOT_FILE_SAVED $BACKUP_DIR/$SNAPSHOT_FILE >> $BACKUP_DIR/$LOGFILE 2>&1
    rm -f $BACKUP_DIR/$SNAPSHOT_FILE_SAVED
fi
# Print end status message for file system backup.
#echo >> $BACKUP_DIR/$LOGFILE
echo "Backup finished" >> $BACKUP_DIR/$LOGFILE
date >> $BACKUP_DIR/$LOGFILE
# Long listing of files in $backup_dir to check file sizes.
ls -alht $BACKUP_DIR  >> $BACKUP_DIR/$LOGFILE

```
 
 
**backup_files_exclude.txt**
 
```
/cdrom
/dev/log
/lost+found
/mnt
/proc
/sys/bus
/sys/class
/sys/devices
/sys/firmware
/sys/fs
/sys/kernel
/sys/module
/sys/power
/tmp
/var/lib/mysql/mydb01data
/var/lib/mysql/mydb02data
/var/lib/mysql/mysql
/var/lib/mysql/phpmyadmin
/var/run
/var/spool
/var/tmp

```
 
**backup_files_include.txt**
 
This file is empty, but must exist.
 
Two final notes:
 
1. The daily backups are overwritten on a weekly basis, the weekly backups are overwritten monthly and the monthly are overwritten annually.
 
2. You will have to edit (a) the script change backup locations and (b) the exclude files txt file so that it matches your particular configuration and needs.
 
Hope this helps you.
 
Regards,
 
John

---

### Post by Fooshnik on 2011-01-27
Thanks. I've been looking into mounting the windows shares via cifs and backing up through ubuntu. If it comes to that I'll have to set up the encryption and everything again so I'm trying to avoid it and stick with windows.

---

### Post by HermanAB on 2011-01-28
Howdy,

The best solution for me, is to install Cygwin on Windows, with OpenSSH and Rsync.  Then I can use rsync to backup stuff.

Note that for Linux, it is only necessary to backup your data.  Backing up the system is quite useless.  It is much easier and faster to freshly install Linux than to restore your old and tired version from backup.

---

### Post by kenbarls on 2011-03-04
I agree with HermanAB. It is the best way/solution I did. I did install the Cygwin on my Windows. And now it works compatible for me. :D

---

