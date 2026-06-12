---
title: "Creating backup of a website on Ubuntu server?"
date: 2015-02-06
forum: Server Platforms
---

### Post by peter1897 on 2015-02-06
I am fairly new to Ubuntu so i have some questions about creating backup of a website:

1. Do i have to backup the whole server or only the website data?
2. Is the incremental backup the best way for making backup?
3. Can i setup mirror backups so i can have my backup data on multiple places like Dropbox, Googledrive and other storage services.
4. What is the easiest way to setup backup that a newbie can handle?

---

### Post by Lars Noodén on 2015-02-06
Only the website data should be necessary.  But keep in mind that if you are using a CMS then that includes the database contents as well as the web pages.

For plain data (images, web pages etc) then rsync is a simple and efficient way to go.  But, again, if there is a database involved then more needs to be done.

You can use rsync to copy data to any writeable file system.  If those storage services show up as a local folder or drive then you are set.  Keep in mind that unencrypted data stored on remote servers will be readable by anyone with access to those servers, both officially and unofficially.

The backup method depends on the data needing to be backed up.  For regular files, I would go with rsync.  There are fancier systems like bacula and such but they are, to me, more work than just using rsync and cron or incron.

---

### Post by peter1897 on 2015-02-06
I will need to backup database data also.

---

### Post by Habitual on 2015-02-06
> **peter1897 said:**
> I will need to backup database data also.
I use something like this...
```
#!/bin/bash
# via root cron - 59 23 * * * /root/name_of_script.sh 
BDATE=$(date +%F)
mysqldump -uroot -p<password> db_name > /path/to/save/mydb-$BDATE.sql
tar -pczf /path/to/save/backup_name-$BDATE.tar.gz /path/to/save/mydb-$BDATE.sql /var/www/ /etc/apache2/sites-enabled/000-default 
rm /path/to/save/mydb-$BDATE.sql
#EOF
```

You can easily save to any medium that has sufficient space.
Adjust /var/www/ /etc/apache2/sites-enabled/000-default according to your environment.

---

### Post by TheFu on 2015-02-07
Lars provides some good info, as usual.

There are as many ways to backup Linux servers as there are Linux servers. It is the admin who decides what is necessary, best for restore, can be automated, and troubleshot at 3am.  After all, I don't have any clue about your website, where the day may be stored, where the DB is, how much extra stuff is involved.  Only the admin knows this stuff.

1 - you probably want to backup enough of the server to get it back exactly as it was before any issue, right?  If you don't care about wasting storage, a full server backup means not having any regrets. If storage is at a premium, it could be useful to reduce the total storage needed for backups. Less to backup, means that backups happen faster too. ;)
2 - Best? Depends. Backups are really the goal. It is all about the restore.  How certain are you that your backups can be restored? That is really the question.
3 - A mirror really isn't enough of a backup for most people. We need versioned backups to fight against hackers, corrupted file systems, accidental deletions, and 1,000 other issues that can happen - oh and if a HDD fails too.  For a website, having 30-120 days of versioned backups is absolutely critical. Without all the versions, after someone hacks the site, how do you determine what happened and when it happened?  Many websites are hacked for months before it is noticed too. Hopefully, your backups will cover all that time.  You can setup anything you like, if you have the technical ability.
4 - Easy?  A few options:
* Pay someone who knows that they are doing.
* Find a friend somewhere with the expertise to help you - a LUG is a good place.  I've helped a few people get their backups working at my LUG. I like to teach, but if they just want me to do it, that's $125/hr.
* learn the different options, deploy a few different ones to see what you prefer. Don't forget to test each as a restore.

I like **rdiff-backup** - it does versioning, but won't push to non-standard locations.  [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best, easiest tutor I've seen. rdiff-backup commands are close to what rsync uses, so I'd use it over rsync for the built-in versioning. rsync can do versioning, if the target file system is Unix and hard links are supported, by creating a script.
**duplicity** features are impressive and it can push to lots of odd storage. Don't recall the list, but S3 was on it and sftp, ssh are too. I found duplicity's near-mandate for encryption difficult, when I didn't want anything encrypted just for my testing. I'm dumb that way. 

There are probably 20 other F/LOSS tools for backups. If you have a tiny bit of data, almost anything can be used.

I don't backup complete servers anymore.  I get the settings, data, files necessary to recreate the server to the same state. This saves about 4G of backup data per server - sometimes more. Restores take about 30-45 min and require skill.  It isn't 1 program, go, and come back, done.  OTOH, one of my servers has 120 days of backups and that takes 65MB of storage - yes - MB. It doesn't have any  data, just settings for spam blocking and filters.

Many people use a hybrid approach - create an image quarterly (must take the system off-line for this or use LVM which is non-trivial), and do settings, data, files daily. This way, getting back to a working system leaves out most skill - restore the image, apply the last data, files and settings backup, then patch to the current level.

The little script Lars posted for mysql backups is close to what I do - except I read the credentials from a file and cleanup old versions automatically.

/root/bin# more backup-redmine-db.sh```

#!/bin/bash
DB_NAME=redmine_default
BACKDIR=/root/backup/
/usr/bin/mysqldump -u root \
    -p`/bin/cat /root/bin/$DB_NAME.passwd.root` $DB_NAME | \
    /bin/gzip > $BACKDIR/${DB_NAME}_`date +%Y%m%d`.gz
    /usr/bin/find $BACKDIR -type f -name $DB_NAME\* -atime 60 -exec /bin/rm {} \;
```

Anyway - those are my opinions. There are lots of posts here with different ideas about server backups.
Please don't backup for years without testing the restore. I see that all to often - usually when the restore failed for some reason and most of the critical data is long gone.

---

### Post by Lars Noodén on 2015-02-08
> **TheFu said:**
> The little script Lars posted for mysql backups is close to what I do - except I read the credentials from a file and cleanup old versions automatically.

In this thread it was Habitual's post with a script.  Though mine also been nice and short.

---

### Post by TheFu on 2015-02-08
> **Lars Noodén said:**
> In this thread it was Habitual's post with a script.  Though mine also been nice and short.

Apologies to everyone.

Plus my script above only puts the DB backup file somewhere - it doesn't actually backup any of the website.  the output location in my script is a critical part of the total backup area - I store settings and lists of packages in the /root/backup/ directory.  Here's exactly what is in that location, on that real box .... 
```
crontab.thefu
crontab.root
dpkg.list
lshw.list
redmine_default_20141210.gz
redmine_default_20141211.gz
redmine_default_20141212.gz
redmine_default_20141213.gz
redmine_default_20141214.gz
redmine_default_20141215.gz
redmine_default_20141216.gz
redmine_default_20141217.gz
redmine_default_20141218.gz
,,,,
redmine_default_20150205.gz
redmine_default_20150206.gz
redmine_default_20150207.gz
redmine_default_20150208.gz

```
My crontab, root's crontab, hardware config, at the bottom of the lshw, I append the **df** output too. Then there are the 60 days of redmine DB backups. They are relatively small - under 200K.  I always backup /root. The exact locations I grab are:
```
my $backup_sources  = "--include /root
--include /etc
--include /usr/local
--include /var/www
--include /usr/share/redmine
--include /var/lib/redmine
--include /home";
```
As you can guess, this is a redmine server (actually a RoR system) and our backup scripts are perl. The key is to get all the areas you need or might need and any configs necessary for a restore.

---

