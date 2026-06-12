---
title: "incremental backup script"
date: 2013-03-10
forum: Server Platforms
---

### Post by kman3107 on 2013-03-10
So I found this 13 year old script and thought I'd use it.
I did my 4 edits and was wondering if this will do the job?
```
[COLOR=#880000]#!/bin/bash[/COLOR]
[COLOR=#880000]# full and incremental backup script[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# created 07 February 2000[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Based on a script by Daniel O'Callaghan <danny@freebsd.org>[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# and modified by Gerhard Mourani <gmourani@videotron.ca>[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]#Change the 5 variables below to fit your computer/backup[/COLOR][COLOR=#000000]
COMPUTER[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]ubuntu                                                 [/COLOR][COLOR=#880000]# name of this computer[/COLOR][COLOR=#000000]
DIRECTORIES[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"/home"                                             [/COLOR][COLOR=#880000]# directoris to backup[/COLOR][COLOR=#000000]
BACKUPDIR[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/media/[/COLOR][COLOR=#000000]temporary[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]backup                        [/COLOR][COLOR=#880000]# where to store the backups[/COLOR][COLOR=#000000]
TIMEDIR[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/media/[/COLOR][COLOR=#000000]temporary[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]backup[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000088]last[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]full                 [/COLOR][COLOR=#880000]# where to store time of full backup[/COLOR][COLOR=#000000]
TAR[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/bin/[/COLOR][COLOR=#000000]tar                                                         [/COLOR][COLOR=#880000]# name and locaction of tar[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]#You should not have to change anything below here[/COLOR][COLOR=#000000]
PATH[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/usr/[/COLOR][COLOR=#000088]local[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#008800]/usr/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]:[/COLOR][COLOR=#008800]/bin
DOW=`date +%a`                          # Day of the week e.g. Mon
DOM=`date +%d`                          # Date of the Month e.g. 27
DM=`date +%d%b`                   # Date and Month e.g. 27Sep
# On the 1st of the month a permanet full backup is made
# Every Sunday a full backup is made - overwriting last Sundays backup
# The rest of the time an incremental backup is made. Each incremental
# backup overwrites last weeks incremental backup of the same name.
#
# if NEWER = "", then tar backs up all files in the directories
# otherwise it backs up files newer than the NEWER date. NEWER
# gets it date from the file written every Sunday.

# Monthly full backup
if [ $DOM = "01" ]; then
                NEWER=""
                $TAR $NEWER -cf $BACKUPDIR/[/COLOR][COLOR=#000000]$COMPUTER[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]$DM[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]tar $DIRECTORIES
[/COLOR][COLOR=#000088]fi[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Weekly full backup[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000088]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#000000] $DOW [/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"Sun"[/COLOR][COLOR=#666600]];[/COLOR][COLOR=#000088]then[/COLOR][COLOR=#000000]
                NEWER[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]""[/COLOR][COLOR=#000000]
                NOW[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]`date +%d-%b`[/COLOR][COLOR=#000000]
                [/COLOR][COLOR=#880000]# Update full backup date[/COLOR][COLOR=#000000]
                echo $NOW [/COLOR][COLOR=#666600]>[/COLOR][COLOR=#000000] $TIMEDIR[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]$COMPUTER[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]full[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]date
                $TAR $NEWER [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]cf $BACKUPDIR[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]$COMPUTER[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]$DOW[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]tar $DIRECTORIES
[/COLOR][COLOR=#880000]# Make incremental backup - overwrite last weeks[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000088]else[/COLOR][COLOR=#000000]
                [/COLOR][COLOR=#880000]# Get date of last full backup[/COLOR][COLOR=#000000]
                NEWER[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"--newer `cat $TIMEDIR/$COMPUTER-full-date`"[/COLOR][COLOR=#000000]
                $TAR $NEWER [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]cf $BACKUPDIR[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]$COMPUTER[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]$DOW[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]tar $DIRECTORIES
[/COLOR][COLOR=#000088]fi[/COLOR]
```Basicly I want to backup /home to my external drive once a day everyday and only backing up new or changed files and folders in /home except on sundays and the 1st of every month when I want a full new backup. Now I don't really need that and could easily go for a weekly incremental backup on sundays with a full backup on the 1st of every month but this is the only full script I've found since most people send noobs like me to guides that would teach us how to make these our selves.

If anyone have any scripts they would like to share with me that does something close to this I'd love to check it out.

Don't bother telling me about programs, apps or stuff like that since I already know of loads of other easier ways to do this. I want to learn this script buisness.

EDIT: Also this script is supposed to be called "something.cron" and be placed in "/etc/cron/daily"

---

### Post by rubylaser on 2013-03-10
If you really just want full and incremental backups I'd just suggest using rsnapshot (but you said you wanted to do this yourself in BASH, so this probably isn't for you).  If you wanted to do it by hand with a BASH script, I would use a combination of rsync and hardlinks. Either way, I'd put these in the root's crontab.
```
sudo -i
crontab -e
```

---

### Post by kman3107 on 2013-03-10
So basicly since I'm impatient and have been reading up on crontab and rsync I think I might have found a suiting command except one thing. I can't get it to actually compress.

What I'm using now:
```
* 01 * * * rsync --delete -azvv /dir-I-backup /dir-I-backup-to
```
All I want now is to find out how to actually compress it and to send it over my network.

---

### Post by rubylaser on 2013-03-10
Rsync's -z option is for compressing during the transfer.  If this is staying on the same box, I wouldn't even use the -z option. If you want to rsync it to a different box for backups, just send it in this format.

```
rsync -avz [COLOR=#000000][FONT=Ubuntu Mono]/dir-I-backup root@192.168.0.56:/dir-I-backup-to[/FONT][/COLOR]
```
Or, just checkout rsnapshot as I mentioned previously. Again, this will not be compressed on the receiving end, rsync only compresses the data for the transfer, it's uncompressed on the other end. 
 
If you want compressed backups, using tar or [duplicity]("http://duplicity.nongnu.org/") are probably better solutions.

---

### Post by kevdog on 2013-03-11
As mentioned above you might want to use duplicity if you want compressed backups. The problem with compressed backups is that it's hard to know exactly what's in the backup since all you get is one big file.  You have to untar and or unzip the backup to see what's inside. Compare this to rsync for example that basically can mimic the original file structure and you have access to the backed up files immediately.  Rsync is basically a syncing utility, rdiff-backup and rsnapshot do both a sync and keep histories of the syncs by storing diffs between the backups.  Rdiff-backup and rsnapshot differ so you might want to take a look at them.  Duplicity uses rdiff-backup as the backend but compresses and can even encrypt the backup with GPg encryption.  Encrypted backups might be handy if you store your backups remotely.

---

### Post by kman3107 on 2013-03-11
Okay. I've come to the conclusion that I'll be using rsync for daily backups and tar for a full weekly backup.
But now that I'm testing my scripts I see that tar is doing it's job but rsync is only taking backups of some files. (would be alright if I already had a full backup but I don't) I was under the impression that rsync made sure that ALL files and folders in directory-A were copied to directory-B.
Right now I get a 11.5kb folder when using rsync on /home, but I get 153.2MB file using tar.
```
#!/bin/bash

# What to backup.
backup_files="/home"

# Backup destination.
dest="/media/temporary/usbbackup"

# Backup name.
date=$(date +%d-%m)
name=$"backup"
archive_file="$name-$date.tgz"

# Make backup using tar.
tar -cvpzf $dest/$archive_file $backup_files

# Find and delete old backups.
find . -name 'backup_*' -mtime +13 -delete

# Print end status message.
echo
echo "Backup finished"
date

# Long listing of files in $dest to check file sizes.
ls -lh $dest
```So this is my almost final weekly backup script.
Since I'm a total noob I'd like inputs on if this will do what I want (you can read in the script what I think the commands do) .  I've run it using terminal and it does backup. But I'm not able to see if the "Find and delete old backups" command works. Also I can't seem to find anything about naming the file anything other then the hostname or any kind of domainname, so I could use an input there. I want the file to be called "backup-date.tgz"

I've found how to name the file in script above and changed the appropriate section.
Still could use input on the "find and delete" command. 

```
#!/bin/bash

#############################################
#        ##       ##            #
#        # # Syn #            #
#        ##      #            #
#        # #      ##            #
#############################################

# What files to sync.
backup_files="/"

# Where to sync files.
dest="user@192.168.0.1:/user/backup"

Password:123

# Print status message.
echo
echo "Backup starting"
date

# Make backup using rsync.
rsync -azv -e ssh --delete $backup_files $dest

# Print end status message.
echo
echo "Backup finished"
date
```This is my rsync script. Will this work? I don't have an ssh setup so I can't check.

---

### Post by kevdog on 2013-03-13
Is there a reason you want to tar/gz your backup rather than just mirror it with rsync?  With tar.gz files, the backup isn't easily searchable if you would need to restore a file -- you want have to extract the file and then find the file you want.  I get you are trying to save space, however you lose easy searchability and restore with the tar.gz archives.  And the way your script is written -- aren't just really creating a tar.gz archive and then rsyncing the entire tar.gz file??? Doesnt this just really break the utility of bandwidth preservation of rsync that really only wants to sync changes (after the initial copy)?  Just some thoughts.  It would seem to me everything you want to do with this script, could be done much easier (still through scripts or bash shell files) using some tool like duplicity that inherently uses rsync and tar.gz.  One of duplicities main advantages is the ability to create gpg encrypted tar.gz archives with rsync, however there is an option with duplicity that you can choose not to use encryption -- with the --no-encryption flag.   If your not into creating differential archives with duplicity (again another feature to create incremental archives (similar to git), you can run duplicity with the --full option everytime to create a full backup -- not just a differential.  This in effect would be creating a tar.gz file on the server transported using rsync.  

I'm not trying to yank your chain, however I'm just suggesting other tools for backup beyond the simple tar.gz files combined with rsync.  Utilities such as rsnapshot, rdiff-backup, duplicity all grew out of the basic rsync protocol, but were developed for inherent limitations with simply rsync -- some tools wanted incremental backups, others wanted maximum space savings via creating of differential backups (with an incremental feature), and others wanted to encrypt the backups since the server might be a public server.  I get you are trying to save space, however you lose easy searchability and restore with the tar.gz archive.  Fortunately if you are one of those do it yourself kind of guys, all these command line tools are best executed with use of scripts because many if not all have various options you must pass on the command line to the program, and its really painful to type the full command line everytime.

---

### Post by rubylaser on 2013-03-13
> **kevdog said:**
> Utilities such as rsnapshot, rdiff-backup, duplicity all grew out of the basic rsync protocol, but were developed for inherent limitations with simply rsync -- some tools wanted incremental backups, others wanted maximum space savings via creating of differential backups (with an incremental feature), and others wanted to encrypt the backups since the server might be a public server.

+1 Very well said.  I would just use duplicity or rsnapshot and have a nice, tested solution working in about 5 minutes.

---

### Post by kevdog on 2013-03-15
One thing I was playing around with the other day was an extension to rdiff-backup called rdiff-backup-fs that allows to mount the rdiff-backups as a filesystem, and hence browse the actual rdiffs as files than just plain rdiffs.  This is a fuse level module.  It's then easy to extract lets say one file from the backup and restore it via a cp command and such.  I wish a utility like this would work with duplicity -- with the added layer that the fuse filesystem would decrypt the backups and then mount them similar to rdiff-backup.  Here is the webpage for the project BTW if you have no idea what I'm talking about: [https://code.google.com/p/rdiff-backup-fs/](https://code.google.com/p/rdiff-backup-fs/)

---

### Post by DanHorniblow on 2013-03-15
I wrote a tutorial on my site a while ago about backup scripts.

You might find it usefull, here is the link.

[http://danhorniblow.co.uk/backup-directories-and-mysql-databses/]("http://danhorniblow.co.uk/backup-directories-and-mysql-databses/")

---

