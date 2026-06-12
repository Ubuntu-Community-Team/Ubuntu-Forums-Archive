---
title: "RLBackup (Rsync Local Backup). An easy way to backup your system"
date: 2008-09-06
forum: Tutorials
---

### Post by SilverWave on 2008-09-06
[FONT=Arial Black][SIZE=3]RLB[/SIZE][/FONT]
This script is the result of wanting a simple backup solution.
For this I needed an efficient way of running rsync for local backups.

My idea was to keep it simple, hence using only bash & rsync.
But also to log useful information so I could easily verify success.

[FONT=Arial Black][SIZE=3]Usage[/SIZE][/FONT]
Create the directories:
/backup/dr/Backups
/backup/dr/myscripts/

Down load the script (rlbackup1script.sh) and exclusion file (rlbackup1exclude.txt).
put both in /backup/dr/myscripts/
Configure backup1script.sh see "Set-up" below

At a terminal enter the command to get a root session:

$ sudo -i

Then run the script:

# /backup/dr/myscripts/rlbackup1script.sh

First time this will take a while, after that not so so long :)


[FONT=Arial Black][SIZE=3]Set-up[/SIZE][/FONT]
To change the defaults just open the script(rlbackup1script.sh) in gedit and update any of the 3 configuration values - that's it :)

```
SOURCE=/
DESTPATH=/backup/dr/Backups
EXCLUDEFILE=/backup/dr/myscripts/rlbackup1exclude.txt
```[FONT=Arial Black][SIZE=3]Details and Help follow:[/SIZE][/FONT]
1. The source path (SOURCE)
    e.g
    /
    what do you want to backup?
    This example would backup the whole system.

2. The destination path (DESTPATH)
    e.g
    /media/medion1/Backups
    Where do you want the backup to be saved to?
    This example would backup to my external USB hard drive.

3. The exclude file path (EXCLUDEFILE)
    e.g
    /media/medion1/Backups/rlbackup1exclude.txt
    A file listing directories I don't want backed up (1 line per item).
    /home/*/.gvfs /home/*/.mozilla/firefox/*/Cache home/*/.thumbnails
    /home2 /home3 /backup /backup2 /windows /lib/modules/*/volatile/*
    /lost+found /media /mnt /proc /sys /tmp/ /var/run /var/lock

__________________________________________________

[FONT=Arial Black][SIZE=2]This script produces a log to help you confirm what has been backed-up etc..[/SIZE][/FONT]

[FONT=Arial Black][SIZE=3]Here is an example RLB Log [/SIZE][/FONT]

```
/backup/dr/Backups
/backup/dr/Backups

rsync -ahvv --log-file=/backup/dr/Backups/back-2008-09-06_18-18-50-LOGFILE.txt --link-dest=/backup/dr/Backups/current-0 --exclude-from=/backup/dr/myscripts/rlbackup1exclude.txt --stats / /backup/dr/Backups/back-2008-09-06_18-18-50

LINK: -File: `/backup/dr/Backups/current-0' -> `back-2008-09-06_18-12-34'
EXTRACT0: -/backup/dr/Backups/back-2008-09-06_18-12-34
LINK: -File: `/backup/dr/Backups/current-1' -> `back-2008-09-06_15-19-38'
EXTRACT1: -/backup/dr/Backups/back-2008-09-06_15-19-38
LINK: -File: `/backup/dr/Backups/current-2' -> `/backup/dr/Backups/back-2008-09-05_23-43-57'
EXTRACT2: -/backup/dr/Backups/back-2008-09-05_23-43-57
============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  176G  260G  41% /backup

============================================================

Backup started:

Sat, 06 Sep 2008 18:18:50 +0100

Backup finished:

Sat, 06 Sep 2008 18:21:32 +0100

============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  176G  260G  41% /backup

============================================================

Statistics

Number of files: 541664
Number of files transferred: 9
Total file size: 36.32G bytes
Total transferred file size: 5.81M bytes
Literal data: 5.81M bytes
Matched data: 0 bytes
File list size: 13255164
File list generation time: 113.077 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 22.65M
Total bytes received: 3.58M

sent 22.65M bytes  received 3.58M bytes  161.42K bytes/sec
total size is 36.32G  speedup is 1384.68


Number of files transferred:9

2008/09/06 18:20:46 [31266] >f..t...... home/sww/.glipper/history
2008/09/06 18:20:46 [31266] >f..t...... home/sww/.wapi/shared_data-silver-Linux-x86_64-328-11-0
2008/09/06 18:20:46 [31266] >f..t...... home/sww/.wapi/shared_fileshare-silver-Linux-x86_64-40-11-0
2008/09/06 18:21:12 [31266] >f.st...... root/.recently-used.xbel
2008/09/06 18:21:12 [31266] >f..t...... root/.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml
2008/09/06 18:21:12 [31266] >f..t...... root/.gconfd/saved_state
2008/09/06 18:21:12 [31266] >f.st...... root/.gnome2/gedit-metadata.xml
2008/09/06 18:21:32 [31266] >f.st...... var/log/auth.log
2008/09/06 18:21:32 [31266] >f.st...... var/log/syslog


Number of Excludes:38

[sender] hiding directory lost+found because of pattern /lost+found
[sender] hiding directory home2 because of pattern /home2
[sender] hiding directory windows because of pattern /windows
[sender] hiding directory proc because of pattern /proc
[sender] hiding directory home3 because of pattern /home3
[sender] hiding directory backup because of pattern /backup
[sender] hiding directory tmp because of pattern /tmp/
[sender] hiding directory mnt because of pattern /mnt
[sender] hiding directory sys because of pattern /sys
[sender] hiding directory media because of pattern /media
[sender] hiding directory backup2 because of pattern /backup2
[sender] hiding directory home/sww/.thumbnails because of pattern home/*/.thumbnails
[sender] hiding file home/sww/.gvfs because of pattern /home/*/.gvfs
[sender] hiding directory home/sww/.mozilla/firefox/khgde814.Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (4).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (font).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (3).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (config speedups done).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (2noLiveMarkBug).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (1disk.capacity).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/0rg5qtzf.clean/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (4 php).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding directory home/sww/.mozilla/firefox/khgde814 (tabs right).Default User/Cache because of pattern /home/*/.mozilla/firefox/*/Cache
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/wl.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/nvidia_new.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/nvidia_legacy.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/nvidia.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fglrx.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcpci.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcdslusb2.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcdslusb.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcdslslusb.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcdslsl.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/fcdsl2.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/ath_hal.ko because of pattern /lib/modules/*/volatile/*
[sender] hiding file lib/modules/2.6.24-19-generic/volatile/.mounted because of pattern /lib/modules/*/volatile/*
[sender] hiding directory var/lock because of pattern /var/lock
[sender] hiding directory var/run because of pattern /var/run

============================================================

Sat, 06 Sep 2008 18:21:32 +0100

Actual usage for the last 4 backups:
36G    /backup/dr/Backups/back-2008-09-05_23-43-57
556M    /backup/dr/Backups/back-2008-09-05_23-43-57
496M    /backup/dr/Backups/back-2008-09-06_15-19-38
228M    /backup/dr/Backups/back-2008-09-06_18-12-34
196M    /backup/dr/Backups/back-2008-09-06_18-18-50
37G    total

Sat, 06 Sep 2008 18:23:49 +0100


Done.

============================================================

[FONT=Arial Black][SIZE=2]Here are some useful bits of the log highlighted: 

The actual rsync command the script ran.[/SIZE][/FONT]
[code]rsync -ahvv --log-file=/backup/dr/Backups/back-2008-09-06_18-18-50-LOGFILE.txt --link-dest=/backup/dr/Backups/current-0 --exclude-from=/backup/dr/myscripts/rlbackup1exclude.txt --stats / /backup/dr/Backups/back-2008-09-06_18-18-50


```[FONT=Arial Black][SIZE=2] Statistics[/SIZE][/FONT]
```
Number of files: 541664
Number of files transferred: 9
Total file size: 36.32G bytes
Total transferred file size: 5.81M bytes
Literal data: 5.81M bytes
Matched data: 0 bytes
File list size: 13255164
File list generation time: 113.077 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 22.65M
Total bytes received: 3.58M

sent 22.65M bytes  received 3.58M bytes  161.42K bytes/sec
total size is 36.32G  speedup is 1384.68



```[FONT=Arial Black][SIZE=2]Disk Usage[/SIZE][/FONT]
```
Sat, 06 Sep 2008 18:21:32 +0100

Actual usage for the last 4 backups:
36G    /backup/dr/Backups/back-2008-09-05_23-43-57
556M    /backup/dr/Backups/back-2008-09-05_23-43-57
496M    /backup/dr/Backups/back-2008-09-06_15-19-38
228M    /backup/dr/Backups/back-2008-09-06_18-12-34
196M    /backup/dr/Backups/back-2008-09-06_18-18-50
37G    total

Sat, 06 Sep 2008 18:23:49 +0100

============================================================


```__________________________________________________

[/code][FONT=Arial Black][SIZE=3]Deleting Backups:[/SIZE][/FONT]
You can delete any backup without affecting others.
If you delete the newest backup you will need to:
Create a symbolic link to it called "current-0"
If this isn't done rsync does a full backup - no hard-linking.

[FONT=Arial Black][SIZE=3]Troubleshooting:[/SIZE][/FONT]
Check the start of the log this gives the rsync command you ran.
Investigate and see if the options and arguments are correct.
Check how many files were transferred & which directories hidden.
Check how much Free Space is detailed in the log.
Run from a terminal to see any error messages (I run from a root terminal).


[FONT=Arial Black][SIZE=3]Background[/SIZE][/FONT]
While researching rsync and hard-linking I came across this article:
"Time Machine for every Unix out there" 
[http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)
Like so many brilliant ideas it was deceptively simple, just 4 lines of code!
The key insight was the way a link was created to point to the new backup.
This link saved the previous directory name between runs of the script.
This is essential to make backups efficiently by hard-linking.

Also interesting is this article by mike rubel:
"Easy Automated Snapshot-Style Backups with Linux and Rsync"
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

Also see rsnapshot [http://www.rsnapshot.org/](http://www.rsnapshot.org/)
A business strength snapshot solution (depends on perl, logrotate & rsync).

[FONT=Arial Black][SIZE=3]The bash script[/SIZE][/FONT]
```
 #!/bin/bash

 # rlbackup
 # (Rsync Local Backup or RLB)
 # Based on 4 lines of code from "Time Machine for every Unix out there"
 # <http://blog.interlinked.org/tutorials/rsync_time_machine.html>
 # 
 # Just fill in the next 3 configuration values - that's it :)

 SOURCE=/
 DESTPATH=/backup/dr/Backups
 EXCLUDEFILE=/backup/dr/myscripts/rlbackup1exclude.txt

 # === Usage ===
 #
 #   0. Do not use spaces in any of the configuration values!
 #     e.g 
 #    This is OK:  DESTPATH=/media/medion1/disasterrecovery/Backups
 #
 #     This is NOT: DESTPATH=/media/medion1/disaster recovery/Back ups
 #                                                   ^             ^
 #     This is NOT: DESTPATH="/media/medion1/disasterrecovery/Back ups"
 #                                                                 ^
 #   1. The source path (SOURCE)
 #    e.g
 #    /
 #    what do you want to backup?
 #    This example would backup the whole system.
 #
 #   2. The destination path (DESTPATH)
 #    e.g
 #    /media/medion1/Backups
 #    Where do you want the backup to be saved to?
 #    This example would backup to my external USB hard drive.
 #
 #   3. The exclude file path (EXCLUDEFILE)
 #    e.g
 #    /media/medion1/Backups/rlbackup1exclude.txt
 #    A file listing directories I don't want backed up (1 line per item).
 #    /home/*/.gvfs /home/*/.mozilla/firefox/*/Cache home/*/.thumbnails
 #    /home2 /home3 /backup /backup2 /windows /lib/modules/*/volatile/*
 #    /lost+found /media /mnt /proc /sys /tmp/ /var/run /var/lock 

 # === Preferences ===
 # You can leave these set to the defaults.
 #
 # If set to "0" this will list Apparent size of backup and actual usage.
 # If set to "4" this will list Actual usage for the last 4 backups.
 # If set to "9" this will list Actual usage for all backups.
 PREF_DISKUSAGE=4

 # If set to "1" this will list the size of each directory.
 # Does not add much time but adds a long list to the RLBLOG.
 PREF_DIRLIST=0

 # If set to "1" then open log in editor
 # Open Editor once backup complete, but continue processing the log.
 # NOTE: If you are using this script with crontab you may wish to set both to "0".
 PREF_POPUP1=0

 PREF_POPUP2=1

 # Set your text editor
 PREF_EDIT="gedit"

 
 # === Notes ===
 # This script is the result of wanting a simple backup solution.
 # For this I needed an efficient way of running rsync for local backups.
 #
 # My idea was to keep it simple, hence using only bash & rsync.
 # But also to log useful information so I could easily verify success.
 #
 # Logs:
 # Most of the useful information is written to RLBLOG which is quite small.
 # LOGFILE is rsync's own built in log (10x smaller than OUTPUTLOG). 
 # OUTPUTLOG is just that.
 # rlberror.log is only created if there are validation errors.
 #
 # Deleting Backups:
 # You can delete any backup without affecting others.
 # If you delete the newest backup you will need to:
 # Create a symbolic link to it called "current-0"
 # If this isn't done rsync does a full backup - no hard-linking.
 #
 # Troubleshooting:
 # Check the start of the log this gives the rsync command you ran.
 # Investigate and see if the options and arguments are correct.
 # Check how many files were transferred & which directories hidden.
 # Check how much Free Space is detailed in the log.
 # Run from a terminal to see any error messages (I run from a root terminal).
 #
 # While researching rsync and hard-linking I came across this article:
 # "Time Machine for every Unix out there" 
 # <http://blog.interlinked.org/tutorials/rsync_time_machine.html>
 # Like so many brilliant ideas it was deceptively simple, just 4 lines of code!
 # The key insight was the way a link was created to point to the new backup.
 # This link saved the previous directory name between runs of the script.
 # This is essential to make backups efficiently by hard-linking.
 #
 # Also interesting is this article by mike rubel:
 # "Easy Automated Snapshot-Style Backups with Linux and Rsync"
 # <http://www.mikerubel.org/computers/rsync_snapshots/>
 # 
 # Also see rsnapshot <http://www.rsnapshot.org/>
 # A business strength snapshot solution (depends on perl, logrotate & rsync).



 # ===> No need to alter anything below this point <===



 # User input validation
 # Check if string is zero length and that directory or file exits.
 if [ -z $DESTPATH ] || [ ! -d $DESTPATH ] ; then
    echo -n "DESTPATH ERROR - "
    echo "Backup destination does not exist or you don't have permission!"
    date -R >> rlberror.log
    echo -n "DESTPATH ERROR - "
    echo "Backup destination does not exist or you don't have permission!" >> rlberror.log
    echo "Exiting..."
    exit 2
 fi


 if [ -z $SOURCE ] || [ ! -d $SOURCE ]; then
    echo -n "SOURCE ERROR - "
    echo "Backup source does not exist or you don't have permission!"
    date -R >> rlberror.log
    echo -n "SOURCE ERROR - "
    echo "Backup source does not exist or you don't have permission!" >> rlberror.log
    echo "Exiting..."
    exit 2
 fi
 

 if [ -z $EXCLUDEFILE ] || [ ! -r $EXCLUDEFILE ]; then
    echo -n "EXCLUDEFILE ERROR - "
    echo "Backup exclude file does not exist or you don't have permission!"
    date -R >> rlberror.log
    echo -n "EXCLUDEFILE ERROR - "
    echo "Backup exclude file does not exist or you don't have permission!" >> rlberror.log
    echo "Exiting..."
    exit 2
 fi

 # Build Backup Strings
 DATE=`date "+%Y-%m-%d_%H-%M-%S"`
 BACKUPNAME=$DESTPATH/back-$DATE
 OUTPUTLOG=$BACKUPNAME-OUTPUT.txt
 RLBLOG=$BACKUPNAME-RLBLOG.txt
 LOGFILE=$BACKUPNAME-LOGFILE.txt
 LINE="============================================================"
 

 # Build Options String.
 OPT_FLAGS=-ahvv
 OPT_LOGFILE=--log-file=$LOGFILE
 #OPT_DEL=--delete
 OPT_LINKDEST=--link-dest=$DESTPATH/current-0
 OPT_EXCLUDE=--exclude-from=$EXCLUDEFILE
 OPT_STATS=--stats
 
 OPT="$OPT_FLAGS $OPT_LOGFILE $OPT_DEL $OPT_LINKDEST $OPT_EXCLUDE $OPT_STATS"

 # Functions.
 print_dat()
 {
     echo >> $RLBLOG
     date -R >> $RLBLOG
     echo >> $RLBLOG
 }

 print_s()
 {
    info="$1"
     echo $info >> $RLBLOG
 }

 print_sn()
 {
    info="$1"
     echo -n $info >> $RLBLOG
 }

 getlinkinfo()
 {
    linfo="$1"
    LINKINFO="Nothing"
    TEMP_EXTRACT="Nothing"
    # could use readlink
    LINKINFO=$(stat $DESTPATH/$linfo | grep "$linfo")
    print_sn "LINK: -"
     print_s "$LINKINFO"
    TEMP_EXTRACT=`expr match "$LINKINFO" '.*\(back-....-..-.._..-..-..\)'`
 }

 # cd to main directory (mainly redundant).
 print_s $DESTPATH
 cd $DESTPATH
 pwd >> $RLBLOG
 
 # Save to RLBLOG the arguments and options you are running.
 print_s
 print_s "rsync $OPT $SOURCE $BACKUPNAME"
 print_s

 # Find last backup directory fron link.
 getlinkinfo "current-0"
 EXTRACT0=$DESTPATH/$TEMP_EXTRACT
 print_sn "EXTRACT0: -"
 print_s $EXTRACT0

 getlinkinfo "current-1"
 EXTRACT1=$DESTPATH/$TEMP_EXTRACT
 print_sn "EXTRACT1: -"
 print_s $EXTRACT1

 getlinkinfo "current-2"
 EXTRACT2=$DESTPATH/$TEMP_EXTRACT
 print_sn "EXTRACT2: -"
 print_s $EXTRACT2

 print_s $LINE

 # Save to RLBLOG the disk space before the backup.
 print_s
 print_s "Free Space on $DESTPATH"
 df -h $DESTPATH >> $RLBLOG
 print_s
 print_s $LINE
 
 print_s
 print_s "Backup started:"
 print_dat

 # The main rsync command
 rsync $OPT $SOURCE $BACKUPNAME > $OUTPUTLOG
 rm $DESTPATH/current-2
 mv $DESTPATH/current-1 $DESTPATH/current-2
 mv $DESTPATH/current-0 $DESTPATH/current-1
 ln -s back-$DATE $DESTPATH/current-0

 # Save to RLBLOG the time and disk space after the backup.
 print_s "Backup finished:"
 print_dat
 print_s $LINE

 print_s
 print_s "Free Space on $DESTPATH"
 df -h $DESTPATH >> $RLBLOG
 print_s
 print_s $LINE

 # Save to RLBLOG the tail of OUTPUTLOG & LOGFILE.
 print_s
 print_s "Statistics"
 tail -n15 $OUTPUTLOG >> $RLBLOG
 print_s

 #print_s
 #tail -v -n50 $LOGFILE >> $RLBLOG
 #print_s

 # Save to RLBLOG a grep of LOGFILE showing the files transferred.
 print_s
 print_sn "Number of files transferred:"
 grep -c '] >f' $LOGFILE >> $RLBLOG
 print_s
 grep '] >f' $LOGFILE >> $RLBLOG
 print_s

 # Save to RLBLOG a grep of OUTPUTLOG showing hidden directories.
 print_s
 print_sn "Number of Excludes:"
 grep -c '] hiding' $OUTPUTLOG >> $RLBLOG
 print_s
 grep '] hiding' $OUTPUTLOG >> $RLBLOG
 print_s
 print_s $LINE

 print_dat

 # View backup results but continue processing the rest of the log.
 if [ $PREF_POPUP1 -eq 1 ]; then
    print_s
     print_s "<======> backup has completed so view the results <======>"
    print_s "<======> ......continuing to process the log..... <======>"
    print_s
     $PREF_EDIT $RLBLOG &
 fi


     # Save to RLBLOG the Total size of 4 backups.
 if [ $PREF_DISKUSAGE -eq 4 ]; then
     print_s "Actual usage for the last 4 backups:"
     du -shc $EXTRACT2 $EXTRACT2 $EXTRACT1 $EXTRACT0 $BACKUPNAME >> $RLBLOG
     print_dat

     # Save to RLBLOG the Total size of all backups.
 elif [ $PREF_DISKUSAGE -eq 9 ]; then
     print_s "Actual usage for all backups:"
     du -shc back-* >> $RLBLOG
     print_dat
 else
    # Save to RLBLOG the Total size of this backup.
     print_s
     print_s "Apparent size of backup and actual usage:"
     du -shc $BACKUPNAME $BACKUPNAME >> $RLBLOG
     print_dat
 fi
 print_s $LINE

 # Save to RLBLOG the usage for each directory.
 if [ $PREF_DIRLIST -eq 1 ]; then
    print_dat
     print_s "Directory List"
     du -h $BACKUPNAME >> $RLBLOG
    print_dat
 fi

 # gzip the logs and move them into the backup folder (to keep things tidy).
 gzip -c $OUTPUTLOG > $OUTPUTLOG.gz
 gzip -c $LOGFILE > $LOGFILE.gz
 mv $OUTPUTLOG.gz $BACKUPNAME
 mv $LOGFILE.gz $BACKUPNAME
 
 # delete the original, uncompressed logs
 rm $OUTPUTLOG
 rm $LOGFILE

 print_s
 print_s "Done."
 mv $RLBLOG $BACKUPNAME

 # View backup results.
 if [ $PREF_POPUP2 -eq 1 ]; then
     $PREF_EDIT $BACKUPNAME/back-$DATE-RLBLOG.txt &
 fi



```[FONT=Arial Black][SIZE=3]An Example Exclude File[/SIZE][/FONT]

```
/home/*/.gvfs
/home/*/.mozilla/firefox/*/Cache
home/*/.thumbnails
/home2
/home3
/backup
/backup2
/windows
/lib/modules/*/volatile/*
/lost+found
/media
/mnt
/proc
/sys
/tmp/
/var/run
/var/lock

```Tested on Ubuntu 8.04/8.10/9.04/9.10/10.04 64 bit.

---

### Post by SilverWave on 2009-03-17
Just a note to advise that this how to has been extensively revised for readability.

---

### Post by kendon on 2009-08-08
nice script, i was just about to write one, but i think i will be using this, saves me some time. thx.

---

### Post by nmayorga on 2009-08-18
Hi!

When using the script I have got a "problem": :confused: 

I am using an external disk for my local backup with rsync, which I plug into the computer via usb. Then, I am the disk's "owner" but its group is root and I have no permissions to chgrp (not even sudoing the command). Hence, when running the script, the terminal window shows a huge number of messages such as

 rsync: chgrp "/media/TREKSTOR/bckp/elemmire/Backups/opt/back-2009-08-18_13-31-07/opt" failed: Operation not permitted (1)

Is there any way to avoid it? Does it matter, by the way?

Furthermore, at the beginning of the script's operation, it displays the following messages:

stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-0': No such file or directory
stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-1': No such file or directory
stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-2': No such file or directory
--link-dest arg does not exist: /media/TREKSTOR/bckp/elemmire/Backups/opt/current-0

Should I create those directories before running the script for the first time?

Thanks a lot in advance,

                           Nacho

---

### Post by SilverWave on 2009-08-22
> **nmayorga said:**
> Hi!

When using the script I have got a "problem": :confused: 

I am using an external disk for my local backup with rsync, which I plug into the computer via usb. Then, I am the disk's "owner" but its group is root and I have no permissions to chgrp (not even sudoing the command). Hence, when running the script, the terminal window shows a huge number of messages such as

 rsync: chgrp "/media/TREKSTOR/bckp/elemmire/Backups/opt/back-2009-08-18_13-31-07/opt" failed: Operation not permitted (1)

Is there any way to avoid it? Does it matter, by the way?



At a terminal enter the command to get a root session:

$ sudo -i

Then run the script:

# /backup/dr/myscripts/rlbackup1script.sh

(Be aware that this way of using root is officially frowned upon).

---

### Post by SilverWave on 2009-08-22
> **nmayorga said:**
> Hi!
Furthermore, at the beginning of the script's operation, it displays the following messages:

stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-0': No such file or directory
stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-1': No such file or directory
stat: cannot stat `/media/TREKSTOR/bckp/elemmire/Backups/opt/current-2': No such file or directory
--link-dest arg does not exist: /media/TREKSTOR/bckp/elemmire/Backups/opt/current-0

Should I create those directories before running the script for the first time?

Thanks a lot in advance,

                           Nacho

Hi 

current-0 is created after the 1st backup.
current-1 is created after the 2nd backup.
current-2 is created after the 3rd backup.

Each time you backup they are renamed to link to the last 3 backups.

---

### Post by Mies on 2009-11-03
Thanks, I'm giving this a try right now.

Edit : Just what the doctor ordered.

---

### Post by scooter28 on 2010-10-04
Old thread I know, but I was wondering how you restore using this backup script. i.e. if I back up from / but only need to restore my boot partition or /home, how would I do that? I probably should have asked before I used the script and set up the cron job, but I figured better late then never.

---

### Post by david.macquigg on 2010-11-11
Excellent script.  I really like the logging features.  There seems to be a problem with the --link-dest option in rsync, however.  It is really slow, and makes the backup consume a lot of space on the destination disk, even if only a few files have changed.   See the discussion at [http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4), especially my post on Nov 10th, where I compare RLBackup to a modified script using cp.

---

### Post by SilverWave on 2010-11-18
> **david.macquigg said:**
> Excellent script.  I really like the logging features.  

Cheers glad you like it.

> **david.macquigg said:**
> 
There seems to be a problem with the --link-dest option in rsync, however.  It is really slow, and makes the backup consume a lot of space on the destination disk, even if only a few files have changed.   See the discussion at [http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4), especially my post on Nov 10th, where I compare RLBackup to a modified script using cp.

__________________

I think you have a problem related to your drive :sad: 

e.g. its very slow for some reason.

---

### Post by SilverWave on 2010-11-18
> **scooter28 said:**
> Old thread I know, but I was wondering how you restore using this backup script. i.e. if I back up from / but only need to restore my boot partition or /home, how would I do that? I probably should have asked before I used the script and set up the cron job, but I figured better late then never.

Well the quick answer is any way you like, as they are just files that can be copied as normal.

Or you can have a look at my restoration plan below...
__________________

 My plan if I need to copy more than a few files is:

1. Install Ubuntu via LiveCD (So I am immediately back in business).
2. Copy /home (bits of etc and anything else I need) from my backup USB Drive.
3. Reinstall all my old applications with one click. [Install Packages from a list]("http://bit.ly/aYUyQ4")

For 2. I will probably just use the RLB script with altered source and destinations info (and no link destination).

__________________

Other ideas...

This sounds good as well, but I haven't tried it yet.

> **paulisdead said:**
> When you do the restore, the /proc and /sys   folders need to exist, but don't need anything in them.  They're not   actually folders on the disk, but a representation of the running kernel   in memory.

If I've got a full backup including the binaries, or just want to   transfer an existing install to another drive, I wouldn't do a full   reinstall.  In the past, I took a livecd, partition the drive, mount all   the partitions into the running livecd's os to somewhere like   /mnt/ubuntu.  Then I copy all the files back into place.  It's very   important to make sure your backups preserve permissions, and when you   restore that you keep the original permissions.  A 'cp -Rp' will do it   (note the capital R, so it picks up hidden files/folders), as will   'rsync -ar' work.  Once the files are copied in place, you need to fix   up the fstab.  Use blkid to determine the new UUIDs of the partitions,   and then put them into the new fstab.  You then need to mount /proc and   /dev from the livecd's folders into the copied folder for the next  step.   You can do it like this 'mount -o bind /proc /mnt/ubuntu/proc'.   The  final step is to reinstall the bootloader by cd'ing into the new  install  and chroot into it, 'chroot /mnt/ubuntu /bin/bash' then a  grub-setup  && grub-install should do it, and you can exit and  unmount  everything and reboot.

__________________

A Note about copying and permissions:

[QUOTE=nilleso]
**cp -p** and/or **scp -p** will probably work for you

*...from cp man page*
-p    Preserve. cp  duplicates  not  only  the  contents  of
      source_file,  but  also  preserves the owner and group
      id, permission modes, modification  and  access  time,
      ACLs,  and  extended attributes, if applicable. Notice
      that the command may fail if ACLs are copied to a file
      system  without  appropriate support. The command will
      not fail if unable to  preserve  extended  attributes,
      modification  and access time, or permission modes. If
      unable to preserve owner and group  id,  cp  will  not
      fail,  and  it  will clear S_ISUID and S_ISGID bits in
      the target. cp will  print  a  diagnostic  message  to
      stderr  and return a non-zero exit status if unable to
      clear these bits.

      In order to preserve the owner and group  id,  permis-
      sion  modes,  and modification and access times, users
      must have the  appropriate  file  access  permissions.
      This  includes being superuser or the same owner id as
      the destination file.
[http://www.linuxquestions.org/questions/linux-newbie-8/copy-files-retaining-ownership-permissions-480735/](http://www.linuxquestions.org/questions/linux-newbie-8/copy-files-retaining-ownership-permissions-480735/)[/QUOTE]

---

### Post by david.macquigg on 2010-11-19
My last backup took an hour and 50 minutes, transferring 2476 files, total 160MB.  Then it took an additional 51 minutes to check the disk usage.  du reports 206M, so I assume 46M is in the directory tree.
```
$ sudo du -shc $BNAME $BNAME
5.0G    back-2010-11-19_02-05-01
206M    back-2010-11-19_02-05-01
5.2G    total
```
Here are some typical backups from the last few days:
```
Date     # Files   MB Transferred     Time(hr:min)  du -shc
11-10      167       239               0:33           0:14
11-14       33        50               0:56           0:31
11-16      451       220               1:38           0:51
11-19     2476       160               1:50           0:51
```
The times seem to be un-related to the number and size of the files transferred.  Perhaps the times are increasing as the backup files get more spread out on the destination disk.

Question:  Where can I find an explanation of what "du" is doing when the same name is repeated, as above?  I don't see any discussion of this in the man page.

---

### Post by SilverWave on 2010-11-19
> **david.macquigg said:**
> My last backup took an hour and 50 minutes, transferring 2476 files, total 160MB.  Then it took an additional 51 minutes to check the disk usage.  du reports 206M, so I assume 46M is in the directory tree.
[...]
The times seem to be un-related to the number and size of the files transferred.  Perhaps the times are increasing as the backup files get more spread out on the destination disk.

__________________

Answer: I think you have a problem related to your drive :sad: 

e.g. its very slow for some reason.

__________________

My backup time was **6 mins** for 946,163 files (checked) 48,703 new/changed files (Copied)  (Size of copy 3.10Gb).
Note that I am using a hard disk for storing the backup (not a USB disk).

__________________

```
/backup/dr/Backups
/backup/dr/Backups

rsync -ahvv --log-file=/backup/dr/Backups/back-2010-11-19_18-49-26-LOGFILE.txt --link-dest=/backup/dr/Backups/current-0 --exclude-from=/backup/dr/myscripts/rlbackup1exclude.txt --stats / /backup/dr/Backups/back-2010-11-19_18-49-26

LINK: -File: `/backup/dr/Backups/current-0' -> `back-2010-09-26_12-26-33'
EXTRACT0: -/backup/dr/Backups/back-2010-09-26_12-26-33
LINK: -File: `/backup/dr/Backups/current-1' -> `/backup/dr/Backups/back-2009-11-06_22-10-06'
EXTRACT1: -/backup/dr/Backups/back-2009-11-06_22-10-06
LINK: -File: `/backup/dr/Backups/current-2' -> `/backup/dr/Backups/back-2009-10-27_17-59-45'
EXTRACT2: -/backup/dr/Backups/back-2009-10-27_17-59-45
============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  396G   40G  91% /backup

============================================================

Backup started:

Fri, 19 Nov 2010 18:49:26 +0000

Backup finished:

Fri, 19 Nov 2010 18:55:32 +0000

============================================================

Free Space on /backup/dr/Backups
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  399G   37G  92% /backup

============================================================

Statistics

Number of files: 946163
Number of files transferred: 48703
Total file size: 26.20G bytes
Total transferred file size: 3.10G bytes
Literal data: 3.10G bytes
Matched data: 0 bytes
File list size: 22.07M
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 3.12G
Total bytes received: 1.04M

sent 3.12G bytes  received 1.04M bytes  8.52M bytes/sec
total size is 26.20G  speedup is 8.39

``````
============================================================

Fri, 19 Nov 2010 18:55:37 +0000

Actual usage for the last 4 backups:
37G    /backup/dr/Backups/back-2009-10-27_17-59-45
947M    /backup/dr/Backups/back-2009-10-27_17-59-45
3.8G    /backup/dr/Backups/back-2009-11-06_22-10-06
15G    /backup/dr/Backups/back-2010-09-26_12-26-33
3.3G    /backup/dr/Backups/back-2010-11-19_18-49-26
60G    total

Fri, 19 Nov 2010 18:58:06 +0000

============================================================

Done.
```3.3 -3.1 = 200M overhead for the hard links.

---

### Post by SilverWave on 2010-11-19
> **david.macquigg said:**
> Question:  Where can I find an explanation of what "du" is doing when the same name is repeated, as above?  I don't see any discussion of this in the man page.

TBH I don't think I ever did see an explanation for this ;-)

I saw in testing RLB that adding the folder name twice, to the argument list sent to du, gave me 2 output sizes so I added it to to report :-)

I think of it as being related to the directory having both a total disk usage including hard-linked files and a total disk usage excluding hard-linked files...

__________________

BTW I think you have a problem related to your drive :-( 

e.g. its very slow for some reason.

---

### Post by david.macquigg on 2010-11-20
Note: Skip this post.  I think I found the problem.  My backup partition is of type NTFS.  I tried an Ext4 partition, and the original script seems to work.  I'll do some more experiments and confirm later.

> My backup time was 6 mins for 946,163 files (checked) 48,703 new/changed files (Copied) (Size of copy 3.10Gb).

5 MB/sec average throughput.  That's more like what I would expect.  I switched back to your original script for another try, but ran into the same problem with an inability to create hard links on the destination disk.  It works only if the destination is on the same disk (/dev/sda1).  If I make the destination my second internal disk (/dev/sdb1), not only are there no hardlinks, but the permissions and ownership are changed.

Here are some typical files and directories in the backup copy on sda1.  The permissions and ownership are preserved, and the number of hardlinks is correct, since there were two backups prior to this listing.

```
/tmp/testback/current-0/david/ASTR501$ ll
...
drwx------  2 david david 4096 2010-10-21 04:14 images/
-rwxr-xr-x  2 david david 4096 2010-09-23 17:52 ._images*
-rw-r--r--  2 david david 1160 2010-11-01 18:00 ipython_notes.txt
drwxr-xr-x  2 david david 4096 2010-11-01 17:58 Matplotlib/
...
```

And here are the same files after changing only the destination.

```
/media/sdb/RLBackups/test/current-0/david/ASTR501$ ll
...
drwxrwxrwx 1 root root  4096 2010-10-21 04:14 images/
-rwxrwxrwx 1 root root  4096 2010-09-23 17:52 ._images*
-rwxrwxrwx 1 root root  1160 2010-11-01 18:00 ipython_notes.txt*
drwxrwxrwx 1 root root  4096 2010-11-01 17:58 Matplotlib/
...
```

I just noticed that my modified script (using cp -al) has more serious problems than being slow.  It has the same problems as the original in not preserving ownership and permissions.  At least the number of links is correct.

```
/media/sdb/RLBackups/home/david/current-0/ASTR501$ ll
...
drwxrwxrwx  1 root root  4096 2010-10-21 04:14 images/
-rwxrwxrwx 21 root root  4096 2010-09-23 17:52 ._images*
-rwxrwxrwx 21 root root  1160 2010-11-01 18:00 ipython_notes.txt*
drwxrwxrwx  1 root root  4096 2010-11-01 17:58 Matplotlib/
...
```

What do you see from the ll command in one of your backups?

---

### Post by david.macquigg on 2010-11-20
> I think of it as being related to the directory having both a total disk usage including hard-linked files and a total disk usage excluding hard-linked files...

Interesting observation.  However, I don't think du can figure out which directory entries are for original files, and which are links.  All it sees is a link pointing to a file, and a field with the number of links to that file in all directories.  In other words, adding a hard link in directory B to a file originally saved in directory A, makes it impossible to discover which directory had the first link.  All links are equivalent.  At least that is my understanding of how hard links work.

Maybe what is happening here is that when du sees a directory listed twice, instead of just repeating the same information, it totals only files which have a single link.  These would be the newly-created files on the last backup copy.

---

### Post by david.macquigg on 2010-11-20
It looks like the du command is doing something more sophisticated than just looking at the link count.  Here are some tests I just ran on a sequence of four backups using the original script.  The file ._images is linked in all four backups, but it gets counted in only one of the targets of the du command, the target where the file is first seen when all targets are processed in the order specified by the du command.  The summaries at the end of the RLBlog files now make sense.

```
david@david-desktop:/media/SDB5/testback$ du -s *
1217380	back-2010-11-20_09-01-43                   # <--
1656	back-2010-11-20_09-04-37
1660	back-2010-11-20_09-05-34
749856	back-2010-11-20_09-22-01
0	current-0
0	current-1
0	current-2
david@david-desktop:/media/SDB5/testback$ rm back-2010-11-20_09-01-43/david/ASTR501/._images 
david@david-desktop:/media/SDB5/testback$ du -s *
1217376	back-2010-11-20_09-01-43
1660	back-2010-11-20_09-04-37                   # <--
1660	back-2010-11-20_09-05-34
749856	back-2010-11-20_09-22-01
0	current-0
0	current-1
0	current-2
david@david-desktop:/media/SDB5/testback$ rm back-2010-11-20_09-04-37/david/ASTR501/._images 
david@david-desktop:/media/SDB5/testback$ du -s *
1217376	back-2010-11-20_09-01-43
1656	back-2010-11-20_09-04-37
1664	back-2010-11-20_09-05-34                   # <--
749856	back-2010-11-20_09-22-01
0	current-0
0	current-1
0	current-2
david@david-desktop:/media/SDB5/testback$ rm back-2010-11-20_09-05-34/david/ASTR501/._images 
david@david-desktop:/media/SDB5/testback$ du -s *
1217376	back-2010-11-20_09-01-43
1656	back-2010-11-20_09-04-37
1660	back-2010-11-20_09-05-34
749860	back-2010-11-20_09-22-01                   # <--
0	current-0
0	current-1
0	current-2
david@david-desktop:/media/SDB5/testback$ rm back-2010-11-20_09-22-01/david/ASTR501/._images 
david@david-desktop:/media/SDB5/testback$ du -s *
1217376	back-2010-11-20_09-01-43
1656	back-2010-11-20_09-04-37
1660	back-2010-11-20_09-05-34
749856	back-2010-11-20_09-22-01
0	current-0
0	current-1
0	current-2

```

---

### Post by SilverWave on 2010-11-20
> **david.macquigg said:**
> Note: Skip this post.  I think I found the problem.  My backup partition is of type NTFS.  I tried an Ext4 partition, and the original script seems to work.  I'll do some more experiments and confirm later.

Glad you has identified the root cause of the issue :-)

---

### Post by SilverWave on 2010-11-20
> **david.macquigg said:**
> [Files are] counted in only one of the targets of the du command, the target where the file is first seen when all targets are processed in the order specified by the du command.  


Good explanation for: du -s *

But what of the actual RLB code:

 ```
# Save to RLBLOG the Total size of 4 backups.
 if [ $PREF_DISKUSAGE -eq 4 ]; then
     print_s "Actual usage for the last 4 backups:"
     du -shc $EXTRACT2 $EXTRACT2 $EXTRACT1 $EXTRACT0 $BACKUPNAME >> $RLBLOG
     print_dat
```So

$ du -shc $EXTRACT2 $EXTRACT2 $EXTRACT1 $EXTRACT0 $BACKUPNAME

Or expanded:

$ du -shc /backup/dr/Backups/back-2009-10-27_17-59-45 /backup/dr/Backups/back-2009-10-27_17-59-45 /backup/dr/Backups/back-2009-11-06_22-10-06 /backup/dr/Backups/back-2010-09-26_12-26-33  /backup/dr/Backups/back-2010-11-19_18-49-26


```
============================================================

Fri, 19 Nov 2010 18:55:37 +0000

Actual usage for the last 4 backups:
37G   /backup/dr/Backups/back-2009-10-27_17-59-45
947M  /backup/dr/Backups/back-2009-10-27_17-59-45
3.8G  /backup/dr/Backups/back-2009-11-06_22-10-06
15G   /backup/dr/Backups/back-2010-09-26_12-26-33
3.3G  /backup/dr/Backups/back-2010-11-19_18-49-26
60G   total

Fri, 19 Nov 2010 18:58:06 +0000

============================================================
```37G and 947M
I am struggling to find a good way to describe this but how about:
The 37G could be considered the "old usage" and the 947M the "new usage"

[update]

After more testing I think  "Total Usage" and "New Usage" are more accurate descriptions.

So:

The 37G is the "Total Usage" size, 947M the "New Usage" size.

This in turn means that the grand total is over by the  "New Usage" size.
(The total Disk Usage is 60G-947M=59.1G)

---

### Post by david.macquigg on 2010-11-21
> The 37G could be considered the "old usage" and the 947M the "new usage"

I agree that's a good brief explanation for regular users.  For those of us who like to understand what's going on behind the scenes, it won't help.  I'm still puzzling over the details of how these totals are counted.  When I run the exact same "du -shc" command (using real names instead of variables from the script) I get results that are off by a few percent, compared to the output of the script.  Very strange!!

---

### Post by SilverWave on 2010-11-21
Nope you missed my update after more testing :-)

The 37G is the "Total Usage" size, 947M the "New Usage" size (Not old and new).

---

### Post by SilverWave on 2010-11-21
> **david.macquigg said:**
> It looks like the du command is doing something more sophisticated than just looking at the link count.  Here are some tests I just ran on a sequence of four backups using the original script.  The file ._images is linked in all four backups, but it gets counted in only one of the targets of the du command, the target where the file is first seen when all targets are processed in the order specified by the du command.  The summaries at the end of the RLBlog files now make sense.

I wonder if, although all hard-links for a file are considered equal...

...that some hard-links are considered more equal than others ;-)

It could be as simple as deciding that the top hard-link in the table is considered the original.

That is...In normal usage, the totals reported by du are of files which are the top hard-link in the table of hard-links pointing to a file.

If a file is hard-linked but not top link in the table, it is not counted.

If you delete the top hard-link the links all move up one, what was the second link, now becomes the top hard-link and is counted by du.

---

### Post by david.macquigg on 2010-11-21
> **SilverWave said:**
> It could be as simple as deciding that the top hard-link in the table is considered the original.

Except that I don't think there is actually a table of links anywhere.  "stat filename" shows the total number of links to filename, but not any information about each link.  Is there any other command besides "stat" that might reveal any more information about the file or its links?

As I understand it, the count of links acts like a reference count in an object-oriented language.  An object is kept alive as long as the count of references to it remain above zero.  When the last link is deleted, the object is added to the garbage collector's list, and it's resources (memory or disk blocks) are returned to the system as soon as the garbage collector gets around to it.

---

### Post by SilverWave on 2010-11-22
Ah ha! We have a winner!

[How does du determine which hard link to disregard?]("http://superuser.com/questions/211222/how-does-du-determine-which-hard-link-to-disregard")

[QUOTE=alexandru][...] it stores a list of traversed inodes and doesn't revisit the ones already seen.[/QUOTE][QUOTE=alexandru]So it does track inodes in the order it sees them, whether that's alphabetical or otherwise.[/QUOTE][QUOTE=Dennis Williamson]Apparently, when fstat(3) sees that the number of hard links is greater than one, it records the inode number for subsequent matching.[/QUOTE][POSIX - du]("http://www.opengroup.org/onlinepubs/9699919799/utilities/du.html")

>  Files with multiple links shall be counted and written for only one entry. The directory entry that is selected in the report is unspecified. 

---

### Post by SilverWave on 2010-11-22
> **david.macquigg said:**
> Except that I don't think there is actually a table of links anywhere.  "stat filename" shows the total number of links to filename, but not any information about each link.  Is there any other command besides "stat" that might reveal any more information about the file or its links?


[14.2 du: Estimate file space usage](http://www.gnu.org/software/coreutils/manual/html_node/du-invocation.html)

> If two or more hard links point to the same file, only one of the hard links is counted.  The file argument order affects which links are counted, and changing the argument order may change the numbers that du outputs.     

---

### Post by SilverWave on 2010-11-22
.

---

### Post by david.macquigg on 2010-11-22
Nice research, Silver.  I did some more tests (see below), and my hypothesis that du is simply looking at the link counts on each file is wrong.  I'm leaning now toward the explanation that du keeps track of every file it has already counted.  That would explain why it seems to run slow on very large link trees.  There could be in memory some large collection of inodes for files already counted.

Here is the tree I set up for testing.  File f1 was originally in dir1, f2 in dir2, and f3 in dir3.  The links were added later.  By listing the arguments to du in various sequences, we can see that the order in which the files and links were created is irrelevant.  So I'm still sticking with the hypothesis that there is nothing more than a link count associated with each file (no ordered list of links, etc.)
```
david@david-desktop:~/test$ ll dir1
total 20
drwxr-xr-x 2 david david  4096 2010-11-21 23:36 ./
drwxr-xr-x 5 david david  4096 2010-11-21 23:38 ../
-rwxr--r-- 3 david david 12110 2010-11-21 23:37 f1*
david@david-desktop:~/test$ ll dir2
total 32
drwxr-xr-x 2 david david  4096 2010-11-21 23:42 ./
drwxr-xr-x 5 david david  4096 2010-11-21 23:38 ../
-rwxr--r-- 3 david david 12110 2010-11-21 23:37 f1*
-rwxr--r-- 2 david david 12110 2010-11-21 23:38 f2*
david@david-desktop:~/test$ ll dir3
total 44
drwxr-xr-x 2 david david  4096 2010-11-21 23:51 ./
drwxr-xr-x 5 david david  4096 2010-11-21 23:38 ../
-rwxr--r-- 3 david david 12110 2010-11-21 23:37 f1*
-rwxr--r-- 2 david david 12110 2010-11-21 23:38 f2*
-rwxr--r-- 1 david david 12110 2010-11-21 23:38 f3*

david@david-desktop:~/test$ du -c dir1 dir2 dir3
16	dir1
16	dir2
16	dir3
48	total
david@david-desktop:~/test$ du -c dir3 dir2 dir1
40	dir3
4	dir2
4	dir1
48	total
david@david-desktop:~/test$ du -c dir3 dir3 dir3
40	dir3
16	dir3
16	dir3
72	total
david@david-desktop:~/test$ du dir2 dir3 dir1
28	dir2
16	dir3
4	dir1
```
Other observations relevant to RLB:
1) If you list a directory twice, the total shown by -c is incorrect.
2) The size shown for the second and later listings includes files that are linked just once, even if those files have already been counted.

---

### Post by SilverWave on 2010-11-22
I have found the explanation :-)

Here we go:

```
du -sh folder1 folder1 folder2 folder3
```The first size for **folder1** is for files with single links **and** for files with multiple links*.
*I am tempted to say all files with multiple links, but you could have 2 hard links to a file in the same folder. Only the first will be counted.

 The second size for **folder1** is for files with single links only. (du has remembered the inodes for files with multiple links and does not show them again).

The third size for **folder2** is for files with single links and for any files with multiple links that haven't been reported on previously.

__________________

The Rules are:

[LIST]
[*]du notes files with multiple links and will only show them once.
[/LIST]

[LIST]
[*]du will always show files with only one link.
[/LIST]

[LIST]
[*]The total reported with -c is simply the sum of the sizes listed.
[/LIST]
__________________

Well that was fun :D

__________________

Thanks to alexandru; Dave Sherohman; Dennis Williamson; Nimmy Lebby and Slartibartfast on [superuser.com]("http://superuser.com/questions/211222/how-does-du-determine-which-hard-link-to-disregard") for the help.

---

### Post by sloth0815 on 2010-12-03
Hi there,
I am relatively new to Ubuntu and just set up a Ubuntu Server Maverick as my file- and webserver. This script seems great but when I run it (after sudo -i) I get a ton of these error messages:

rsync: failed to hard-link /media/Data/Backup_Jonas/Server/current-0/lib32/libpcre.so with lib32/libpcre.so: Function not implemented (38)

/media/Data/Jonas_Backup/Server is the destination directory.
Any idea what I am doing wrong?

Cheers,
Jonas

---

### Post by SilverWave on 2010-12-04
> **sloth0815 said:**
> Hi there,
I am relatively new to Ubuntu and just set up a Ubuntu Server Maverick as my file- and webserver. This script seems great but when I run it (after sudo -i) I get a ton of these error messages:

rsync: failed to hard-link /media/Data/Backup_Jonas/Server/current-0/lib32/libpcre.so with lib32/libpcre.so: Function not implemented (38)

/media/Data/Jonas_Backup/Server is the destination directory.
Any idea what I am doing wrong?

Cheers,
Jonas

Could you post the rsync command you used please.

Just copy and paste from the top of the log.

Oh and I would recommend 10.04 rather than 10.10 as it is a Long term release.

P.S.

If you are trying to backup to a external drive is it ext3 or ext4?

---

### Post by sloth0815 on 2010-12-04
Thanks for the quick reply. The rsync command is the following:

rsync -ahvv --log-file=/media/Data/Backup_Jonas/Server/back-2010-12-03_11-11-34-LOGFILE.txt --link-dest=/media/Data/Backup_Jonas/Server/current-0 --exclude-from=/home/Jonas/rsync_backupscripts/rlbackup1exclude.txt --stats / /media/Data/Backup_Jonas/Server/back-2010-12-03_11-11-34

All harddrives are internal ext3 pooled with mhddfs and parity protected with flexraid

---

### Post by SilverWave on 2010-12-05
> **sloth0815 said:**
> Thanks for the quick reply. The rsync command is the following:

rsync -ahvv --log-file=/media/Data/Backup_Jonas/Server/back-2010-12-03_11-11-34-LOGFILE.txt --link-dest=/media/Data/Backup_Jonas/Server/current-0 --exclude-from=/home/Jonas/rsync_backupscripts/rlbackup1exclude.txt --stats / /media/Data/Backup_Jonas/Server/back-2010-12-03_11-11-34

All harddrives are internal ext3 pooled with mhddfs and parity protected with flexraid

I would set-up a simple plain ext3/ext4 disk (preferably with 10.04 if you have another spare machine) and see if that works first.

---

### Post by david.macquigg on 2012-02-09
I've been using this excellent script for over a year now to back up my entire system, including Ubuntu 10.04 as a host for VirtualBox and two Windows virtual machines.  I've had a few problems, and found simple solutions, so I thought I would pass these on and hopefully save someone else a major expense.

The costly problem is my backup drive needed to be replaced, and the link tree which holds all the backups could not be copied to the new drive.  The guy at the computer shop said his cloning program (Acronis) saw 90 million files, ran all weekend, and eventually gave up.  The unix cp command has the same problem.  It creates a separate copy for each link in the tree.  After a few hours of futile effort, he gave up, thinking the problem was bad sectors and a corruption of the filesystem.

The solution is to use the command "rsync -aHr".  The H option preserves the hard-links.

The second problem happened when I added virtual machines to my setup.  VirtualBox keeps these virtual machines in huge files on the host system.  RLBackup copies the entire file anytime there is a small change to any file within the VM.  The solution I'm using is to exclude the VM files from the backup, and just run a separate backup utility within each virtual machine.  I'm using Mozy because it is free while the total backup is less than 2GB, and they don't seem to mind that I have a separate free account for my Windows 7 VM.  I don't feel like I am cheating here, because I have a paid account which would easily store the entire system if it could avoid copying the entire VM for every little change.

---

### Post by SilverWave on 2012-02-09
> **david.macquigg said:**
> The guy at the computer shop said his cloning program (Acronis) saw 90 million files, ran all weekend, and eventually gave up.  The unix cp command has the same problem.  It creates a separate copy for each link in the tree.  After a few hours of futile effort, he gave up, thinking the problem was bad sectors and a corruption of the filesystem.

The solution is to use the command "rsync -aHr".  The H option preserves the hard-links.



Class! that’s is so funny :-)


Glad you liked the script.

---

### Post by adrian.h on 2012-04-28
What is the purpose of ***sudo -i***?  What is the need for elevated permissions?  Or is this only required for backing up directories that are not directly accessible to you from your logged in permissions?


A

---

### Post by SilverWave on 2012-04-29
> **adrian.h said:**
> What is the purpose of ***sudo -i***?  What is the need for elevated permissions?  Or is this only required for backing up directories that are not directly accessible to you from your logged in permissions?


A

The following link has some discussion on the subject:

[http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i](http://askubuntu.com/questions/70534/difference-between-su-sudo-s-sudo-i)
> 
su asks for the password of the user "root".
  sudo asks for your own password (and also checks if you're allowed to run commands as root, which is configured through /etc/sudoers -- by default all user accounts that belong to the "admin" group are allowed to use sudo).
  sudo -s launches a shell as root, but doesn't change your working directory.  
sudo -i simulates a login into the root account: your working directory will be /root, and root's .profile etc. will be sourced as if on login.



---

### Post by mike-g2 on 2013-07-11
Just had a HDD fail and the most recent backup through our offsite was several days ago so I'm trying to develop a sensible local back up system to avoid a similar situation.  

Yours looks like a very nice one but I'm wondering if I'll have any issues if I use your script as a cron script (i.e. put it in /etc/cron.daily).  I'm also wondering if there's an easy way to have it automatically remove older back ups once the total size of the back ups reaches a particular size.  I don't want to have to remember to run the script nor clean out old back ups.

Thoughts?

---

### Post by CharlesA on 2013-07-11
I don't think the script will have any problems running via cron, but you should test it first. ;)

As far as deleting old backups goes, I have seen people use date --date=STRING to pass on a date like "one year ago" to a script to do a rm -r if a backup from that date exists.

---

