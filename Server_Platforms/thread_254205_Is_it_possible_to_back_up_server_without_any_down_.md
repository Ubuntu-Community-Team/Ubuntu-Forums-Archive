---
title: "Is it possible to back up server without any down time?"
date: 2006-09-09
forum: Server Platforms
---

### Post by narrowband on 2006-09-09
Is there a command to backup a Ubuntu 6.06 server to a Windows shared folder while it is running.

---

### Post by kidders on 2006-09-09
If what you mean by "server" is the entire filesystem structure of a Ubuntu box, then no. You'd be inviting this kind of (potentially disasterous) scenario:

[LIST=1]
[*]An application (eg an LDAP or MySQL server) has two files open.
[*]You start your backup.
[*]The application begins a modification to both files; one file gets updated.
[*]The backup processes both files.
[*]The second file gets updated.
[/LIST]

Now, while the files themselves are consistent, they won't necessarily make good sense in combination any more :-(

A far better approach would be one of these:

[LIST=1]
[*]Replication - MySQL is a good example, where backups can be made "live" and in real time, rather than incrementally.
[*]Progressive backups - You could start with, say, your web server, shut it down, back up /var/www, and start it up again. Then, you could move on to something else, and so on.
[/LIST]

Any help?

---

### Post by chrisfay on 2006-09-09
Mount the shared folder to the Ubu box using smbfs, and then resync or tar your root directory. You could drop a simple backup script in cron to do it nightly.

---

### Post by narrowband on 2006-09-09
Hi Chrisfay. You can do back ups while running windows using true image so why would Linux be any different?

Hi Kidders. So you say it's possible but Chrisfay disagrees saying there would be potential problems if files are modified during the back up.

Yes by server I did mean the whole root partition.

My server is running Apache, MySQL, Wordpress, Gallery2, MRTG, Smokeing and Cacti. If that helps.

The whole idea of being able to back up while running was to prevent down time. Stopping and starting services would therefore not prevent down time while backing up.

Normally I shutdown the server and boot True Image or Ghost to back up the root partition.

I suppose RAID is another option for a true real-time back up however that would not protect against me braking something or accidentally deleting something.

---

### Post by chrisfay on 2006-09-09
> Hi Kidders. So you say it's possible but Chrisfay disagrees saying there would be potential problems if files are modified during the back up.

You have us backwards...I said you CAN backup your root partition while the OS is running; check the previous posts.

Certain system files will be locked from the backup but for the programs you mentioned it would not be an issue. This is a simple bash script I put in cron to do nightly backups of my system, mail me the completion and output the results to a viewable file on my webserver. Obviously pretty basic but works for me:


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

#let's delete the previous system backup
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
[http://www.cjfay.com/logs/backup_log.txt](http://www.cjfay.com/logs/backup_log.txt)
END

else
        echo "Couldn't find repository directory"
mail -s "System Backup Failed" chrisfay <<-END
System backup failed. /mnt/share probably wasn't mounted
END

fi
exit
```

---

### Post by narrowband on 2006-09-10
Opps sorry I got you mixed up.

I'll have to give that script a go to see how it works.

Thanks

---

### Post by kidders on 2006-09-10
I just thought I'd add a brief word of caution about MySQL servers. Unless you run a very lightly loaded one, you can take it for granted that the on-disk version of the database will always be inconsistent, which means that, should you have to restore a backup, the very first thing MySQL will invariably have to do is repair itself.

From the perspective of someone running a server, making raw file backups also precludes the possibility that you might like to run your server off another Linux box temporarily, while you perform the restore, condemning you to the very thing you're trying to avoid ... downtime.

I can't comment with the same degree of confidence about the other services you mentioned, but imho, relying on the kind of backup you're describing to undo a disaster is quite risky and apparently, very strongly discouraged.

If I were you, I'd simply back up a mysqldump.

---

### Post by Macchi on 2006-09-10
Now perhaps off-topic, but I just would like to mention that RAID increases the reliability and/or performance of a running system but absolutely does NOT eliminate the need for good backups of the information stored in that system.

---

### Post by chrisfay on 2006-09-10
I agree with you in regards to backing up an SQL server as I understand it utilizes memory to store a good portion of data which would be invariably skipped in such a backup. 

That said, there are plenty of other solutions to this matter and I only presented a simple option that has saved me many times after failed config file edits, corruption and accidental deletion. 

The point is, it's doable.

---

### Post by kidders on 2006-09-10
Yep :-)

---

### Post by Balut on 2006-09-10
You may want to take a look at rdiff-backup.  This also won't properly backup an online mysql db, but for standard files it works great.

[http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

