---
title: "Errors using rdiff-backup to Samba Share"
date: 2006-08-20
forum: Server Platforms
---

### Post by chrisfay on 2006-08-20
So I'm having the hardest time backing up using rdiff-backup to my mounted samba share. I can backup with no problems locally which doesn't do me any good. When using my Samba share as my destination directory I get this: 

> Removing backups older than 2 weeks
Fatal Error: Bad directory /mnt/share/rdiff_mirror.
It doesn't appear to be an rdiff-backup destination dir
Starting Backup
Exception 'local variable 'ext_rp' referenced before assignment' raised of class 'exceptions.UnboundLocalError':
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 325, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 602, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 137, in init_readwrite
    self.set_extended_filenames(subdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 208, in set_extended_filenames
    assert not ext_rp.lstat()

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 23, in ?
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main
    take_action(rps)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 325, in Backup
    rpout.conn.fs_abilities.backup_set_globals(rpin)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 602, in backup_set_globals
    dest_fsa = FSAbilities('destination').init_readwrite(Globals.rbdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 137, in init_readwrite
    self.set_extended_filenames(subdir)
  File "/usr/lib/python2.4/site-packages/rdiff_backup/fs_abilities.py", line 208, in set_extended_filenames
    assert not ext_rp.lstat()
UnboundLocalError: local variable 'ext_rp' referenced before assignment
Command exited with non-zero status 1
0.06user 0.01system 0:00.08elapsed 90%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+1662minor)pagefaults 0swaps
Backup Complete

This is the basic script I made to do what I need...anything I'm doing wrong?


```
#!/bin/bash
#Rdiff backup script for automated backups
#written by Chris fay
#8/20/06

# Let's define some variables
backup_dir="/"  # backup directory
repository="/mnt/share/rdiff_mirror"  # directory backing up to
excludes="--exclude /proc --exclude /mnt --exclude /lost+found --exclude /sys --exclude /media"

#Let's mount the Samba Share
sudo mount /mnt/share

#Checking for old backups that need to be removed
echo "Removing backups older than 2 weeks"
sudo rdiff-backup --remove-older-than 2W $repository

#Lets start it up
echo "Starting Backup"
sudo time nice -n +15 rdiff-backup $excludes $backup_dir $repository
echo "Backup Complete"

#send an email notification
mail -s "Rdiff Mirror of Ubuntu Complete" chrisfay <<-END
The complete mirror of Ubuntu has finished
END

exit
```

I have been using this tar script with no issues:

```
#!/bin/bash
# Back that thing up

# Let's Define a Few Variables

BACKUP_DIR="/"  # The directory that nees to be backed up
REPOSITORY="/mnt/share/system_backup"   # The directory where I'll store the backups
DATE=$(date +%b%d)

# Let's mount our samba share /mnt/share
echo "mounting samba share"
sudo mount /mnt/share

#let's delete the old system backup
sudo rm -R $REPOSITORY
sudo mkdir $REPOSITORY

# Do the backup
echo "starting backup"
if [ -d $REPOSITORY ] && [ -s $REPOSITORY ]
  then
        sudo time nice -n +15 tar cfvPz $REPOSITORY/$DATE.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media $BACKUP_DIR >> /var/www/cjfay/logs/backup_log.txt
        echo "Backup for $DATE done."

#Let's send an email notification
mail -s "System Backup of Ubuntu" chrisfay <<-END
The complete backup of Ubuntu Server has finished Successfully:
http://www.cjfay.com/logs/backup_log.txt
END


    else
        echo "Couldn't find repository directory"
mail -s "System Backup Failed" chrisfay <<-END
System backup failed. /mnt/share probably wasn't mounted
END

fi
exit
```


Why would tar work but not rdiff?

---

### Post by manifoldronin on 2006-12-03
Hi Chris, I wonder if you ever found a solution for this problem. I'm getting exactly the same error when trying to rdiff-backup to a mounted samba share (a Windows share).

---

### Post by firebadger on 2006-12-13
Me too!?

---

### Post by chrisfay on 2006-12-13
I dropped my attempt at rdiff and resorted back to a modified tar script. I did however get a PM from a guy who made a suggestion recently. His idea was as follows:

> Would this be the fix
sudo time nice -n +15 rdiff [COLOR="Red"]-v 5[/COLOR] -backup $excludes $backup_dir $repository

Not sure if adding the '-v 5' would make any difference but since I removed everything and all is working fine, I am not re-attempting.

Let me know if this helps and I'll tell the guy who sent me the suggestion.

---

