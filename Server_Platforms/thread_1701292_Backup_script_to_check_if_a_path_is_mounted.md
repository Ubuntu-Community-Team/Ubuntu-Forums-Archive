---
title: "Backup script to check if a path is mounted"
date: 2011-03-06
forum: Server Platforms
---

### Post by Demented ZA on 2011-03-06
I'm writing a script to rsync some directories to external hdd for backup.

My external hdd gets automatically mounted to /media/backup1

My script then backs up predefined directories to /media/backup1.

I have added this script to cron to run once every day.

The problem is that in the case where the drive is not plugged in and the script runs, it backs up to my local hard drive, and since it is more than 70% full, it fills it up by duplicating that 70% onto itself.

I have taken the script further, to test whether /media/backup1 is mounted. If it is, the backup will run. If it is not, it will bail out.

I'm using the mountpoint program to test for mounts.

My script so far:
```
#!/bin/bash
if [[ `mountpoint /media/backup1` ]]; then
       echo "filesystem mounted"

# The backup function. Commented out for testing.
#       rsync --verbose --progress -a /var /media/backup1
#      rsync -a /var /media/backup1/rsync

else
        echo "backup1 not mounted"
fi
```

If /media/backup1 is mounted, and I run the script, it reports "filesystem mounted".

If /media/backup1 is _**NOT**_ mounted, and I run the script, it _**still**_ reports "filesystem mounted".

When /media/backup1 is mounted and I run:
```
$mountpoint /media/backup1
/media/backup1 is a mountpoint
$
```

When /media/backup1 is _**NOT**_ mounted and I run:
```
$mountpoint /media/backup1
/media/backup1 is not a mountpoint
$
```

Clearly, "$mountpoint /media/backup1" works at the command line as expected, but when being executed in the script, it should return 1 when mounted or 0 when not, resulting in an appropriate message, but it doesn't. What am I doing wrong?

---

### Post by CharlesA on 2011-03-06
Hiya,

I think it's echoing that it's mounted because of the way you set it up. It's running mountpoint successfully, instead of checking for a mountpoint and then returning the exit code depending on the result. See the modified script at the bottom of this post. :)

Here's what one of my backup scripts look like (it's nasty but it works):

```
#!/bin/bash

###
### full.sh
### Script to do a full backup of RAID5 Array
### Created by CharlesA
### Tested 10/04/2010
### Updated 10/04/2010
###

BIN=/bin/
USR=/usr/bin/
ARRAYPATH=/array/
FULLPATH=/full/
HOME=/home/charles/
ERROR=${HOME}logs/full_backup_error.log
DATE=$(${BIN}date +%D)
LOG=$(${BIN}date +%m%d%Y)

[COLOR="Red"]# Check if $ARRAYPATH is mounted and, if so, mount full backup drive
if ${BIN}mountpoint -q $ARRAYPATH
then
  { ${BIN}mount -t ext4 UUID=755a6096-908d-4ddd-b7b6-5725c43717f5 $FULLPATH; } 2> $ERROR || { echo "Mounting of backup drive failed"; exit; }
else
  { echo "RAID Array not mounted!"; exit; }
fi[/COLOR]

NEWFULLDIR=$FULLPATH
FULLLOG=${FULLPATH}log/${LOG}.txt

# rync
if ${BIN}mountpoint -q $FULLPATH
then
  { ${USR}rsync --archive --itemize-changes --delete --log-file $FULLLOG $ARRAYPATH --exclude lost+found --exclude log --exclude full.txt $NEWFULLDIR && echo "Full Backup Completed on $DATE" > ${FULLPATH}full.txt  && ${BIN}umount $FULLPATH; } 2> $ERROR || { echo "Full backup failed."; exit; }
fi
# eof

```

I modified your script like so:

```
#!/bin/bash
[COLOR="Blue"]if mountpoint -q /media/backup1
  then
    echo "filesystem mounted"[/COLOR]

# The backup function. Commented out for testing.
#       rsync --verbose --progress -a /var /media/backup1
#      rsync -a /var /media/backup1/rsync

  else
    echo "backup1 not mounted"
fi
```

EDIT 2:

Here's a script that'll work. :)

```
#!/bin/bash

if [[ $(mountpoint -q /media) ]]
  then
    echo mounted
  else
    echo unmounted
fi
```

---

### Post by Demented ZA on 2011-03-06
Awesome, that seems to be all I needed. I was convinced the if statement was where the fault was.

After a little cleanup, this is what it looks like:

```

#!/bin/bash
if mountpoint -q /media/backup1
  then
       echo "filesystem mounted"
       rsync -a /var /media/backup1/rsync

else
       echo "filesystem not mounted"
fi

```

Two questions if I may:


[LIST=1]
[*]is my rsync statement sufficient? Should I add enything else?
[*]This is getting placed in a cron job. How do I go about sending an e-mail to root and another e-mail address to notify that the backup has been completed or failed?
[/LIST]
Thank you once again, the backup is now working :-)

---

### Post by CharlesA on 2011-03-06
In my rsync scripts I tell it to create a log as well as itemized changes (and delete files that aren't there any longer).

Are you just backing up the entire /var/ folder or do you want it to be an exact copy?

In order to send an email you'd have to install a MTA (Mail Transfer Agent - either Postfix or Exim) and write the script so that it'll send an email to root or something else if the backup finishes or fails.

---

### Post by Demented ZA on 2011-03-06
Well I'm trying to do just a backup. Under /var I have folders being shared, users mail and faxes. Everything is being backed up to two hard drives (Backup1 and Backup2). 

I basically don't want the backup drives to be an EXACT copy, as I still want to give the users someplace to go to retrieve an accidentally deleted or lost file.

As for mail, this server is an internet gateway/firewall, mailserver, and fax server, so my MTA is set up and working. I was just asking as I'm not sure how to go about implementing e-mail notifications.

---

### Post by CharlesA on 2011-03-06
Ah ok.

Your rsync command looks fine then.

The way I have mine set up is that it'll email me if the backup fails, and not do anything if the backup was successful.

Your rsync statement would look something like this:

```
rsync -a /var /media/backup1/rsync || echo "Backup Failed for $(date)| mail -s "Backup Failed" someemail@host
```

The "||" tells bash to run that command should the previous command exit with anything that is not 0.

---

### Post by Demented ZA on 2011-03-09
I wish I knew more about perl. Its such a handy tool.

I have expanded a little on the script to allow for two hard-drives. In other words, rotational offsite backup. One drive is left on site, and another off-site. When the manager goes home, she unplugs the drive from the server and takes it home. The next mourning she brings the other drive to work.

```
#!/bin/bash
#               Backup Drive 1

if mountpoint -q /media/backup1
  then
    echo "Backup Drive #1 is mounted."
       rsync -verbose -a /var /media/backup1/rsync
       rsync -verbose -a /home /media/backup1/rsync

else
        echo "Backup Drive #1 not mounted."
fi

#               Backup Drive 2

if mountpoint -q /media/backup2
  then
    echo "Backup Drive #2 is mounted."
       rsync -verbose -a /var /media/backup2/rsync
       rsync -verbose -a /home /media/backup2/rsync

else
        echo "Backup Drive #2 not mounted."
fi
```I will use your solution, but I would need to add additional functionality.

I would like to be notified in detail about the process, as the technical contact i need to keep an eye on things to make sure its working as needed. I suppose I can just have cron e-mail its output to me. Even better, would be to log everything to a file, and have either cron or the script e-mail it to me as an attachment.

Also, I need to send an e-mail to the manager, so that she will know that todays backup has completed, and to which drive. I assume I can just add something like 
```
mail -s "Backup to Backup Drive 1 Completed" someemail@host
```
inside the if statement of the first drive and another similar one to the if statement of the second?


Your help is greatly appreciated. I'm sure other people are finding this useful as well.

---

### Post by CharlesA on 2011-03-09
Well you can use the --log-file switch to tell it where to put the log file.

You can cat it and then pipe it to mail if you desire. I have no experience attaching files from the command line, so I do it that way.

---

### Post by Demented ZA on 2011-03-10
I found sending attachments from terminal to be easy using mutt:

```
mutt -s "Subject" -a test.txt -- name@domain.com
```

I'm going to try output the result for the first two lines of rsync to a file called backup1.txt, and then the second two rsync lines to a file called backup2.txt. Then, directly after I call the second rsync in each statement, I'll invoke mutt to send me a mail, and add the attached files.

I'll post my script here afterwards :-)

Thank you for your help

---

### Post by CharlesA on 2011-03-10
Oh cool. I haven't really messed with mutt all that much. Thanks. :)

---

### Post by Demented ZA on 2011-03-13
How can I consolidate 
```
rsync -verbose -a /var /media/backup1/ 
rsync -verbose -a /home /media/backup1/rsync
```into one line?

will this work?
```
rsync -verbose -a {/var,/home} /media/backup1/
```If I can consolidate those two lines, I won't have to worry about piping the results of the first rsync line to a file, and then appending the results of the second line to that same file in order to produce an e-mail with a single attachment. I could just attach two different files; one per line, but where's the fun in that, right?

---

### Post by CharlesA on 2011-03-13
Not sure how that would work, but I used to use this:

```
rsync -av /var/ /home/ /destination/
```

I think that'll put a var and home folder into destintion.

Don't forget that you can always use --dry-run when testing.

---

### Post by Demented ZA on 2011-03-14
Well using ```
rsync -verbose -a {/home,/var} /media/backup1/rsync
``` actually works fine. I'm using that as its easier to understand.

So far my script looks like this:

```
#!/bin/bash

LOG=$(${BIN}date +%m%d%Y)

#        Backup Drive 1

if mountpoint -q /media/backup1
  then
    echo "Backup Drive #1 is mounted."

       mkdir /media/backup1/rsync/log
       rsync -verbose -a {/home,/var} /media/backup1/rsync > /media/backup1/rsync/log/$LOG.txt
       mutt -s "Backup to Backup Drive 1" -a /media/backup1/rsync//log/$LOG.txt -- myemail@domain.com

else
        echo "Backup Drive #1 not mounted."
fi

#        Backup Drive 2

if mountpoint -q /media/backup2
  then
    echo "Backup Drive #2 is mounted."

       mkdir /media/backup2/rsync/log
       rsync -verbose -a {/home,/var} /media/backup2/rsync > /media/backup2/rsync/log/$LOG.txt
       mutt -s "Backup to Backup Drive 2" -a /media/backup2/rsync/log/$LOG.txt -- myemail@domain.com

else
        echo "Backup Drive #2 not mounted."
fi

```

The logfile is being created and the backups are running exactly as they should, however I'm still having a problem with my notification e-mail. I don't know if mutt is actually sending my e-mail and if its getting stuck at my smtp, or whether something is going wrong when calling mutt.

I suppose I'll have to start logging my cron output, and test it with mailto instead of mutt to see whats going on.

---

### Post by CharlesA on 2011-03-14
Try using regular "mail" and see what happens.

---

### Post by Demented ZA on 2011-03-14
I did, tried it from the terminal and it just got stuck. Looking into /var/log/mail.log, I noticed postfix and my relay host is not happy with each other. My ISP enabled authentication on their smtp server. Now I have a whole new problem: relay host authentication. I started a new thread [here]("http://ubuntuforums.org/showthread.php?p=10558684#post10558684").

Edit: What I failed to mention, is that I have set up postfix to work with authentication, but it keeps saying my login is incorrect, when I know its correct. I suspect something wrong with security.

---

### Post by Demented ZA on 2011-03-17
Thanks to rubylaser, I sorted out my smtp problem.

Now, back to the backup script.

I made some modifications. Basically, aside from testing to see if the drive(s) are mounted, it does the following additional:


[LIST]
[*]Unmounts and re-mounts drives before backup (This is to prevent "dirty" mounts)
[*]Generate's neat e-mail notifications that will be sent to one or many users via e-mail to notify them that the backup finished or failed, when it was performed, and how long it took.
[*]It sends me an e-mail to my main e-mail in case of failure
[*]Rotates logfiles, and backs them up as well.
[/LIST]
Otherwise, cron will, using mutt for mail, e-mail me the output of the job, and attach a text file of the output of the rsync job.

My script looks like this:
```
#!/bin/bash

DATE=$(${BIN}date +%m%d%Y)
STARTDATE=$(${BIN}date +%D)
STARTTIME=$(${BIN}date +%T)
echo 
DURATION=$(${BIN}date)
START=`date +%s`


echo "$ ls -l /media/backup1"
ls -l /media/backup1
echo
echo "$ ls -l /media/backup2"
ls -l /media/backup2
echo

#Just in case mounts are dirty
echo "$ umount /media/backup1"
umount /media/backup1
echo
echo "$ umount /media/backup2"
umount /media/backup2
echo
echo "$ mount /media/backup1"
mount /media/backup1
echo
echo "$ mount /media/backup2"
mount /media/backup2
echo

#        Backup Drive 1

echo "Checking if Backup Drive 1 is mounted"
echo

if mountpoint -q /media/backup1
  then
    echo "Backup Drive 1 is mounted. Starting Backup."
    echo
    DRIVE1=true
       rsync -verbose -a {/home,/var} /media/backup1/rsync > /var/log/backup/$(${BIN}date +%m%d%Y).txt
    cp /var/log/backup/$(${BIN}date +%m%d%Y).txt /media/backup1/rsync/log/

else

        echo "Backup Drive 1 is NOT mounted."
        echo
        DRIVE1=false
fi


#        Backup Drive 2

echo "Checking if Backup Drive 2 is mounted"
echo

if mountpoint -q /media/backup2
  then
    echo "Backup Drive 2 is mounted. Starting Backup."
    echo
    DRIVE2=true
       rsync -verbose -a {/home,/var} /media/backup2/rsync > /var/log/backup/$(${BIN}date +%m%d%Y).txt
    cp /var/log/backup/$(${BIN}date +%m%d%Y).txt /media/backup2/rsync/log/
else
        echo "Backup Drive 2 is NOT mounted."
        echo
        DRIVE2=false
fi


if "$DRIVE1"
 then
   if "$DRIVE2"
     then
       MESSAGE="Company XYZ backup to drive 1 and 2 successful!"
       SUBJECT="Company XYZ backup to drive 1 and 2 successful! $(${BIN}date +%D)"
   else
       MESSAGE="Company XYZ backup to drive 1 successful!"
       SUBJECT="Company XYZ backup to drive 1 successful! $(${BIN}date +%D)"
   fi
else 
   if "$DRIVE2"
     then
       MESSAGE="Company XYZ backup to drive 2 successful!"
       SUBJECT="Company XYZ backup to drive 2 successful! $(${BIN}date +%D)"
   else
       MESSAGE="Company XYZ Backups Failed: $(${BIN}date +%D). This could be because no backup drives were connected. Please make sure they are connected before the next run in three hours. I have notified the administrator of this problem, just in case."
       SUBJECT="Company XYZ Backup FAILED! $(${BIN}date +%D)"
       mutt -s "Backup FAILED! $(${BIN}date +%D)" -- name@domain.com < /dev/null
   fi
fi

STOPDATE=$(${BIN}date +%D)
STOPTIME=$(${BIN}date +%T)
END=`date +%s`

echo "$MESSAGE" && echo " " && echo "Backup started at:  $STARTDATE  $STARTTIME" && echo "Backup finished at: $STOPDATE  $STOPTIME" && echo && echo "Duration in seconds: $(($END-$START))" && echo && echo

(echo "$MESSAGE" && echo " " && echo "Backup started at:  $STARTDATE  $STARTTIME" && echo "Backup finished at: $STOPDATE  $STOPTIME" && echo && echo "Duration in seconds: $(($END-$START))" && echo && echo ) | mutt -s "$SUBJECT" name@domain.com
```

The script runs every 3 hours. All output is captured, and then sent to me using mutt, with the rsync job log in an attached .txt file for easy opening on a Windows machine. This is what my cron entry looks like:
```
1 0,3,6,9,12,15,18,21 * * * perl /var/scripts/backup | mutt -s "Company XYZ Backup" -a /var/log/backup/$(${BIN}date +%m%d%Y).txt -- myemail@mydomain.com
```

This is what the e-mail looks like that is sent to users:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186413&stc=1&d=1300403437[/IMG]

This is what the e-mail to me looks like:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186412&stc=1&d=1300403437[/IMG]

---

### Post by CharlesA on 2011-03-17
Nice job!

---

### Post by rubylaser on 2011-03-17
That's a good looking backup script.  And, I'm glad getting Postfix working contributed to this.  One little thing I'd change is your crontab with all of the hours listed out.  I'd just simplify the beginning like this...
```

00 */3 * * * perl /var/scripts/backup | mutt -s "Company XYZ Backup" -a /var/log/backup/$(${BIN}date +%m%d%Y).txt -- myemail@mydomain.com

```
You certainly can leave it how you have it, I just like to keep my time portions short if I can :)

---

### Post by Demented ZA on 2011-03-22
> **rubylaser said:**
> That's a good looking backup script.  And, I'm glad getting Postfix working contributed to this.  One little thing I'd change is your crontab with all of the hours listed out.  I'd just simplify the beginning like this...
```

00 */3 * * * perl /var/scripts/backup | mutt -s "Company XYZ Backup" -a /var/log/backup/$(${BIN}date +%m%d%Y).txt -- myemail@mydomain.com

```You certainly can leave it how you have it, I just like to keep my time portions short if I can :)

I actually did have it like that, but for some reason when I edit it through webmin, it changes the times back to the way I posted previously. I suppose its because cron differs between distributions, and Webmin is built to be redundant between distributions.

In any case, I've changed the backup times to 10 am after the first drive gets plugged in, and then again at 4pm, just before the users go home.

Backup times are often as quick as a minute. I suppose it could be longer if there are significant changes to source, but that's how long it takes on a typical day's work between 5 users.

The backup script is working nicely. There are maybe some things I'd like to add (code clean-up, better redundancies, more efficient code), but for now its working like a charm.

Thanks for everyone's help!

---

### Post by CharlesA on 2011-03-22
Thanks Demented ZA. Is it ok if I poke thru yer code and see if I can get my backup script working?

Seems I broke something when I tried them on a Debian system (instead of Ubuntu) and now I get to figure out what is wrong so I can fix it.

Might as well add some enhancements if I can.

---

### Post by Demented ZA on 2011-03-23
Sure dude! Knock yourself out. Just please explain the changes here afterwards. Sometimes I can get a little dense if I have a lot on my mind :-p

Edit: Would you mind posting what you've got so far? Output of your script, as well as your cron tab. It'll help if you log the output of cron to a file, and post that as well? Thx!

---

### Post by NedHanlon on 2011-03-23
You could also save the script on the external hdd, that way, if it was not present, the script could not run.

---

### Post by CharlesA on 2011-03-23
Found what was wrong, I forgot a ")" after I added the command to run df -h.

Here's the entire thing:

```
#!/bin/bash

###
### backup.sh
### Script to backup RAID Array
### Created by Charles Auer
### Tested 03/22/2011
### Updated 03/22/2011
###

# Standard Variables
BIN=/bin/
USR=/usr/bin/
# Email Variable
EMAIL=somename@domain.com
# Backup Paths
ARRAYPATH=/array/
DOCPATH=/docback/
DVDPATH=/dvdback/
HOME=/home/charles/
ERROR=${HOME}logs/daily_backup_error.log
# Date Variables
DATE=$(${BIN}date +%D)
FOLDER=$(${BIN}date +%m%d%Y)

# Get Date/Time backup started
STARTDATE=$(${BIN}date +%D)
STARTTIME=$(${BIN}date +%T)
START=$(date +%s)

# Check if RAID Array is mounted
if ${BIN}mountpoint -q $ARRAYPATH
# If Array is mounted, then mount both backup drives
  then
    { ${BIN}mount -t ext4 UUID=49a8cdd0-a4fd-43e5-9c6e-3a4a3363b770 $DOCPATH && ${BIN}mount -t ext4 UUID=32f2ca4f-65c5-4241-8d6d-3c483417e908 $DVDPATH; } 2> $ERROR || { echo "Mounting of backup drives failed" | ${USR}mail -s "Backup failed for $DATE" $EMAIL; exit; }
# If not, email me that the array isn't mounted and that the backup failed
  else
    { echo "Raid Array not mounted!" | ${USR}mail -s "RAID Array not mounted! Backup Failed for $DATE" $EMAIL; exit; }
fi

[COLOR="Blue"]# Gather info about free space of drives
FREESPACE=$(${BIN}df -h | ${BIN}egrep '(Filesystem)|(sd)')[/COLOR]

# Variables for Doc Backup
OLDDOCNAME=$(${BIN}cat ${DOCPATH}latest)
NEWDOCDIR=$DOCPATH$FOLDER
OLDDOCDIR=$DOCPATH$OLDDOCNAME
DOCLOG=${DOCPATH}log/${FOLDER}.txt

# Check if Doc is mounted and if so, do a incremental backup of it.
if ${BIN}mountpoint -q $DOCPATH
  then
    { ${BIN}cp --archive --link $OLDDOCDIR $NEWDOCDIR && echo $FOLDER > ${DOCPATH}latest && ${USR}rsync --archive --itemize-changes --delete --log-file $DOCLOG $ARRAYPATH --exclude dvds --exclude lost+found $NEWDOCDIR && ${BIN}umount $DOCPATH; } 2> $ERROR || { ${BIN}cat $ERROR | ${USR}mail -s "Doc Backup failed for $DATE" $EMAIL; exit; }
fi

# Variables for DVD Backup
OLDDVDNAME=$(${BIN}cat ${DVDPATH}latest)
NEWDVDDIR=$DVDPATH$FOLDER
OLDDVDDIR=$DVDPATH$OLDDVDNAME
DVDLOG=${DVDPATH}log/${FOLDER}.txt

# Check if DVD is mounted and if so, do a incremental backup of it.
if ${BIN}mountpoint -q $DVDPATH
  then
   { ${BIN}cp --archive --link $OLDDVDDIR $NEWDVDDIR && echo $FdailyOLDER > ${DVDPATH}latest  && ${USR}rsync --archive --itemize-changes --delete --log-file $DVDLOG /array/dvds $NEWDVDDIR && ${BIN}umount $DVDPATH; } 2> $ERROR || { ${BIN}cat $ERROR | ${USR}mail -s "DVD Backup failed for $DATE" $EMAIL; exit; }
fi

# Get Date/Time backup completed
STOPDATE=$(${BIN}date +%D)
STOPTIME=$(${BIN}date +%T)
END=$(date +%s)

# Send email of success
# Based on backup notification by Demented ZA
# http://ubuntuforums.org/showthread.php?t=1701292
(echo "Backup started at:  $STARTDATE  $STARTTIME" && echo "Backup finished at: $STOPDATE  $STOPTIME" && echo && echo "Duration in seconds: $(($END-$START))" && echo && echo "Disk Usage:" && echo && echo "$FREESPACE" ) | mail -s "Daily Backup Complete for $DATE" $EMAIL
# eof

```

The email I get daily looks like this:

```
Backup started at:  03/23/11  08:07:29
Backup finished at: 03/23/11  08:16:49

Duration in seconds: 560

Disk Usage:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             442G   47G  374G  11% /
/dev/sdb1             3.6T  2.0T  1.7T  55% /array
/dev/sdd1             1.4T  1.1T  188G  86% /docback
/dev/sdc1             1.8T  1.6T  276G  85% /dvdback


```

I kinda like the how it'll tell me how much space is used/free on the drives.

---

### Post by Demented ZA on 2011-03-23
> **NedHanlon said:**
> You could also save the script on the external hdd, that way, if it was not present, the script could not run.

True, but the way this script works, is by performing functions, and letting myself as well as the user know what's going on in a presentable way, regardless of drive presence.

In the event that nothing is plugged in, I'm notified to my primary e-mail, that there's a problem. Otherwise, e-mails are being sent to an account that I have access to, but seldom do.

As my phone is connected to my e-mails, at two mails a day, that becomes a lot quite quickly if you have 5 or so servers deployed.

Not having the script present to execute as it does negates this functionality.

I like the idea though :-) lateral thinking!

@CharlesA, awesome, glad you came right! Showing available space is quite awesome. I didn't think of that. Would like to add that to mine as well when I have the time :-)

---

### Post by CharlesA on 2011-03-23
I got the idea from [RLB]("http://silverwav.wordpress.com/2010/01/15/rsync-local-backup/").

---

### Post by Catalyph on 2011-12-06
Awesome thanks for the help everyone, Here is the script I made up based on some of the input here

```
#! /bin/bash

#Check for Mounted Drive

if mountpoint -q /media/Backup
    then
        echo "Backup Drive Detected and Mounted"
        echo "Executing Backup with --delete"

#If mounted then run this rsync and create a log file in the home directory

        rsync -rupogh --delete --stats --log-file=/home/UbuntuUser/rsynclog /NAS/ /media/Backup/
    else

#If it is not mounted then attempt to mount it based on the UUID, I did this incase power goes out, I do #not have the drive in FSTab because I like to disconnect it and bring it with me sometimes

        echo "Backup Drive NOT Mounted to /Backup"
        echo "Atempting to Mount Backup Drive"
        mount -U 2252E44921821241 /media/Backup  

#check for it again after attempted mounting 

       if mountpoint -q /media/Backup
            then
                echo "Drive Succesfully Mounted"
                echo "Executing Backup"
                rsync -rupogh --delete --stats --log-file=/home/sintek/rsynclog /NAS/ /media/Backup/
            else
                echo "Drive Not Connected"
                echo "Aborting Backup"
        fi
fi

```

---

### Post by Demented ZA on 2011-12-07
Well done! Glad our efforts have helped :)

---

