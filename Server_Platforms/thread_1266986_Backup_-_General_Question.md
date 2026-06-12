---
title: "Backup - General Question"
date: 2009-09-15
forum: Server Platforms
---

### Post by sevenearths on 2009-09-15
I have files in /var/www/files that belong to www-data:www-data. I would like to:

1. Create a scheduled backup to a limited account (/home/backup/Desktop)
[NOTE: I don't know how to get a lesser user to copy www-data's files. I'm presuming cron and sudoers would help]

2. Create a script in /home/backup/Desktop that, when the backup user logs in, copies the files on the desktop to a removable drive
[NOTE: I presume 'cp -uR --reply=yes /mountedDirectory /backupDirectory' will help me with that]

---

### Post by terazen on 2009-09-15
You could create a script to do a tar backup of the directories to a file in the right location and then change permissions. ```
tar cvpzf /home/backup/Desktop/somefile.tgz /some/dir
chown user:group /home/backup/Desktop/somefile.tgz
```

If you are just copying the directories then you could use cp and then ```
chown -R user:group /home/backup/Desktop/folder
```

Also, are you overwriting the file everytime or do you want to keep backups every day for x amount of days?

---

### Post by sevenearths on 2009-09-16
> **terazen said:**
> You could create a script to do a tar backup of the directories to a file in the right location and then change permissions. ```
tar cvpzf /home/backup/Desktop/somefile.tgz /some/dir
chown user:group /home/backup/Desktop/somefile.tgz
```

If you are just copying the directories then you could use cp and then ```
chown -R user:group /home/backup/Desktop/folder
```

Also, are you overwriting the file everytime or do you want to keep backups every day for x amount of days?

Thanks for the reply. I'm trying to get this sorted ASAP.

I tried what you said but I am having troubles with permissions:

```
arthur@arthur-laptop:~/Desktop/gnomenu$ cp -r /var/www/***/files/ /home/arthur/Desktop/
cp: cannot stat `/var/www/***/files/09/Jul': Permission denied
cp: cannot stat `/var/www/***/files/09/Aug': Permission denied
cp: cannot stat `/var/www/***/files/09/Sep': Permission denied
arthur@arthur-laptop:~/Desktop/gnomenu$ tar cvzf /home/arthur/Desktop/test.tgz /var/www/***/files/
tar: Removing leading `/' from member names
/var/www/***/files/
/var/www/***/files/09/
tar: /var/www/***/files/09/Jul: Cannot stat: Permission denied
tar: /var/www/***/files/09/Aug: Cannot stat: Permission denied
tar: /var/www/***/files/09/Sep: Cannot stat: Permission denied
tar: Error exit delayed from previous errors

*** = web dir
```

I think I need to have a simple backup account be able to execute a backup script as su. Something like:

```
#!/bin/bash
cp -uR --reply=yes --no-preserve=ownership /var/www/***/files /home/backup/Desktop
```

I'm hoping the '-u' on 'cp' will only copy ONLY the new files across.

Eventually I would like to be able to make sequential backups (tgz's). The problem is I would like to date suffix them (don't know how to do that) and delete the old ones if there is more then 30 (don't know how to do that either) :(

---

### Post by terazen on 2009-09-16
You'd need to run it with sudo or a user with permissions.  Arthur doesn't have access it appears.  I'd just use crontab and run as root.

You could try something like this:```
#!/bin/bash
#
DATE=`date +%y%m%d`
NUMDAYS=28
#
tar cvpzf /home/arthur/Desktop/somefile-backup_$DATE.tgz /var/www/somedir/files
chown arthur /home/arthur/Desktop/somefile-backup_$DATE.tgz
#
rm -f `find /home/arthur/Desktop/ -name "somefile-backup_*.tgz" -mtime +$NUMDAYS

```

Also, the script file you use in the crontab it's good to only give root access to it.
```
sudo chmod 700 filename
sudo chown root:root filename
```

I think this is what you are looking to do.

---

### Post by sevenearths on 2009-09-17
Thats is genius. Thank you!

Am I right in thinking that a cron task will run as the user that created the crontab/task. 

i.e. If root creates a script and then cron runs that script. That script will be run as if it were root. Correct?

+ Why do you advise making the script 700? Why should I care if other people double click the script and make backups?

---

### Post by sevenearths on 2009-09-17
Quick Question:

You know when you do 'sudo su'. Are you actually root, or are you a user acting as root? And is there a difference?

[This]("http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way") kind of answered my question but doesn't tell me that if I do this whether I will actually be root. If you are in the root shell, does that mean your logged into the system and are root?

---

### Post by terazen on 2009-09-17
Sudo runs tasks with root privileges if your user is listed in the /etc/sudoers file.

For the crontab, it depends how you set it up.  This is for a simple sql backup to run *as root* at 11:30pm from one of my server's /etc/crontab file.

```
# m h dom mon dow user  command
30 23   * * *   root    /bin/sqlbackup
```

About the 700 permissions, anything in crontab that runs automatically as root every day I'd try to be careful with.  It takes up cpu and will overwrite files if run more than once in a day.  Also, for the script to work you'll need to be root anyways so if someone doesn't have sudo access then they really have no need.

---

### Post by terazen on 2009-09-17
This is from the initial portion of "man sudo":

> NAME
       sudo, sudoedit - execute a command as another user
.....

DESCRIPTION
       sudo allows a permitted user to execute a command as the superuser or another user, as specified in
       the sudoers file.  The real and effective uid and gid are set to match those of the target user as
       specified in the passwd file and the group vector is initialized based on the group file (unless the
       -P option was specified).  If the invoking user is root or if the target user is the same as the
       invoking user, no password is required.  Otherwise, sudo requires that users authenticate themselves
       with a password by default (NOTE: in the default configuration this is the userâs password, not the
       root password).  Once a user has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes unless overridden in sudoers).

---

### Post by sevenearths on 2009-09-18
> **terazen said:**
> You'd need to run it with sudo or a user with permissions.  Arthur doesn't have access it appears.  I'd just use crontab and run as root.

You could try something like this:```
#!/bin/bash
#
DATE=`date +%y%m%d`
NUMDAYS=28
#
tar cvpzf /home/arthur/Desktop/somefile-backup_$DATE.tgz /var/www/somedir/files
chown arthur /home/arthur/Desktop/somefile-backup_$DATE.tgz
#
rm -f `find /home/arthur/Desktop/ -name "somefile-backup_*.tgz" -mtime +$NUMDAYS

```

Also, the script file you use in the crontab it's good to only give root access to it.
```
sudo chmod 700 filename
sudo chown root:root filename
```

I think this is what you are looking to do.

I managed to implement this method by creating the above script in /root/Desktop/ (with 700) and opening up cron (crontab -e) and adding:

```
0 23 0 0 1,4 /root/Desktop/backup.sh
```

The only thing is you are missing a small tick from the last line on the bin/bash. You couldn't tell me where it goes could you?

---

### Post by terazen on 2009-09-18
Doh, woops.  After the find command.

rm -f `find /home/arthur/Desktop/ -name "somefile-backup_*.tgz" -mtime +$NUMDAYS`

---

### Post by sevenearths on 2009-09-21
Thanks I think that answers all my questions

---

### Post by sevenearths on 2009-10-14
I thought I'd open up this post again because I've trying to learn bash but have just been to busy lately.

The situation is:

 - I have a folder on my desktop called 'backup' (/home/xxx/Desktop/backup)
 - I have a folder with all documents submitted online called 'files' (/var/www/webfolder/files)
 - The 'files' folder is divided up chronologically by the php that uploads the files (e.g. /var/www/webfolder/files/09/Jul, /var/www/webfolder/files/09/Sep)

I would like to create a bash script that runs every day (cron - 11pm) and looks for all files that have been created that same day in /var/www/webfolder/files and then adds them to a date indexed zip file (ddmmyy.tgz) in /home/xxx/Desktop/backup. I know I can do this with a combination of 'find -ctime' and 'cp', but I'm not to sure how.

Any ideas?

---

### Post by sevenearths on 2009-10-14
I found the following that helps but it doesn't help when your files have spaces :(

```

tar cvf /home/bob/files.tar `find /home/bob -mtime -1 -type f`
```

---

### Post by sevenearths on 2009-10-14
I found that if I 'cd' into the right directory I could use the following:

```
find -name '* *' -type f -mtime 0 -exec tar -cvf some.tar {} +
```

Thanks go to [Greg Miller]("http://unixjunkie.blogspot.com/2007/01/handling-filenames-with-spaces_15.html")

---

