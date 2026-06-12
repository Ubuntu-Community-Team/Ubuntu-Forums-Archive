---
title: "Backup to AmazonS3"
date: 2016-09-13
forum: Server Platforms
---

### Post by neodjandre on 2016-09-13
I am thinking of using this program [http://s3tools.org/usage](http://s3tools.org/usage)
to backup my Ubuntu 16 server to Amazon S3. I have 1GB of RAM.

I will have a cron job to run every midnight.

Newbie Question: Is it OK to backup the entire server / (root) or should I only use var/www ?

many thanks,
Andrew

---

### Post by howefield on 2016-09-13
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by Habitual on 2016-09-13
> **neodjandre said:**
> I am thinking of using this program [http://s3tools.org/usage](http://s3tools.org/usage)
to backup my Ubuntu 16 server to Amazon S3. I have 1GB of RAM.

I will have a cron job to run every midnight.

Newbie Question: Is it OK to backup the entire server / (root) or should I only use var/www ?

many thanks,
Andrew
The cost incurred in EC2 is data outbound from the instance/region/AZ, so....
However, there is no need to archive your whole system ("/")
/home/<user> and /var/www/ and 
run
```
apache2ctl -S
```in termnal and grab apache's sites' .conf files listed there.

databases? 
```
mysqldump -uroot -p <db> > /path/to/file.sql
```
dumps one db per file.

So, in summary:
/home/andrew/
/etc/apache2/sites-enabled/000-default.conf
/var/www/*
and dbs using mysqldump per db, or just include /var/lib/mysql/* in the backup if not being written to.

See also [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by neodjandre on 2016-09-13
thanks for the tips. I am using Digital Ocean droplet and transfer of files is free.. Could you please explain why there is no need to backup the entire system ("/"). If something bad happens to the server, how could I rebuild the whole system?

---

### Post by Habitual on 2016-09-13
> **neodjandre said:**
> If something bad happens to the server, how could I rebuild the whole system?
Why backup a possible exploit/rootkit/compromised package, from a system you know to be b0rked?

That's not backup at all.
And if you don't fix the cause, it doesn't matter what you backup. 
And no matter what you store, any where, encrypt before "Send"

"If" erm, [COLOR=#ff0000]when[/COLOR] sh*t happens...
I always assume the server is cracked/rooted/whatever and that dictates [COLOR=#ff0000]re-install from scratch[/COLOR].
**It's the only way to be sure**.

Trust me.

See also [https://www.digitalocean.com/community/tutorials/how-to-use-digitalocean-snapshots-to-automatically-backup-your-droplets](https://www.digitalocean.com/community/tutorials/how-to-use-digitalocean-snapshots-to-automatically-backup-your-droplets)

---

### Post by neodjandre on 2016-09-14
ok that makes total sense! sorry for being such a n000b

---

### Post by Habitual on 2016-09-14
> **neodjandre said:**
> ok that makes total sense!
If something I said makes "sense" to you, then we haven't wasted anything.
I usually advise "new users" who "get it", don't use the label "n00b".
And only be sorry you used the word. :)

It's derivative and ugly.
Former term: llamah 
Definition: Can't even install Linux.
I couldn't you know, back in the '90s. Slackware v-smth-early.0
I screwed the pooch so many times. It was painful to learn.
Redhat, same thing.
Couldn't tell you if "less is 'more'" (it is) if it was tattooed on my forehead in reverse.

Find a better label, amigo :)
"BoFH in Training" (you may earn BoFH much later) is "Edgy", I guess.
You are very welcome.

[Sound advice]("https://ubuntuforums.org/showthread.php?t=510812").

Peace.

---

### Post by SeijiSensei on 2016-09-14
How much disk space do you have available?  The 1 GB of memory doesn't tell us anything useful.

I routinely back up these directories from my remote servers to a drive attached to my home office server:
```

etc/
home/
var/log
var/spool
var/lib/pgsql/backups

```
You can ignore /var/spool if the server isn't handing mail.  I dump both the MySQL and PostgreSQL servers running on that machine to /var/lib/pgsql/backups. The websites I host all reside in directories under /home, so I'm not including /var/www in my list. YMMV.

---

### Post by TheFu on 2016-09-14
Definitely encrypt before sending to any hardware that isn't in a physical location that you control.

I do not backup entire systems either. I do backup whatever is necessary to rebuild the system in 30-45 minutes, however.
What gets backed up is a little different for each system, but generally, it is
[LIST=1]
[*]A current HW configuration - including partitions, storage, and lshw
[*]Everything under /etc/
[*]A list of packages installed
[*]/root/ - I tend to put scripts there
[*]/home - if there are any home directories; I usually exclude caches and "local object storage"; Most servers don't have much under /home/ since I don't give out access to normal users.
[*]Anywhere that has extra data that isn't in the above locations.
[*]Any crontabs - these are usually in /var/spool/cron ... but I just dump them using crontab -l
[/LIST]

Sometimes there are DBs - I'll either shutdown the DB or dump their contents to a date-stamped file and gzip it.   If gzip'd, the file would be placed under /root/backups/ so it gets picked up in the normal backup.  That means having daily backups that slowly rotate through the normal backup retention period.  I keep 2 weeks of MariaDB dumps (14 complete dumps.gz) - so that means every backup set has 15 copies of the DB with various dates.  DBs are the life of most servers and usually tiny.  My blog with 2.5K articles and all public pages and images is ... 221MB (uncompressed). That's nothing.

On systems that cannot be taken offline during the backups, don't forget to use LVM snapshots as a way to get a completely static file system that can be safely backed up.

And encrypt all backups before shipping them to any "cloud storage."  Keep the encryption keys somewhere else. I like to change the key used daily with a static part and a dynamic part that can be created easily.  Longer is better.

---

### Post by Habitual on 2016-09-15
Thanks Fu
I missed the crons and /etc/*

dbs too!
/var/lib/mysql/*

---

### Post by TheFu on 2016-09-15
> **Habitual said:**
> Thanks Fu
I missed the crons and /etc/*

dbs too!
/var/lib/mysql/*

Yep. Learned that after a restore failure. Had a communications system that had about 50 contabs entries across 5 different management accounts (lots of F/LOSS made up the system) crash. Thought I had everything necessary to restore, but didn't have the crontabs - ouch.  Quickly updated all my backup scripts (each system has a slightly customized version) to get crontabs and perl cpan modules lists and ruby gem lists - if the areas where those are installed are outside the normal backup areas.  Sometimes grabbing /var/www/ or /opt/ is easier.

I really hope people are switching away from MySQL.  There are alternatives like MariaDB and ACID DBs like Postgres for more critical data. Not many people here seem to use noSQL DBs, but those "document-based" DBs need to be backed up too.

Did I mention - always "pull" backups, don't "push" them. Better for security. Don't want the hacked box having access to the backup storage, after all.

---

### Post by SeijiSensei on 2016-09-15
> **TheFu said:**
> I really hope people are switching away from MySQL.  There are alternatives like MariaDB and ACID DBs like Postgres for more critical data.
Unfortunately there are still major applications like WordPress which expect a MySQL backend.  Apparently it's possible to use PostgreSQL, but there are a lot of hoops to jump through, and WP itself has lots of mysqli() function calls written into the PHP code.  I would love to dump the MySQL instance on my server and just use PG for everything, but it's not always possible.

I began using PostgreSQL back around 1995 or so when MySQL was still not freely licensed.  As a result I couldn't sell clients a server running MySQL without paying licensing fees.  I started using PostgreSQL and have continued to do so unless forced to use something else as is the case with WordPress.

---

### Post by TheFu on 2016-09-15
Last time I check, MariaDB was a binary compatible drop in for MySQL.  To all clients, it appears to be mysql. The mysql client-side connections are used to connect to mariaDB.  [https://mariadb.com/kb/en/mariadb/mariadb-vs-mysql-compatibility/](https://mariadb.com/kb/en/mariadb/mariadb-vs-mysql-compatibility/)  There are always a few exceptions where it isn't exactly the same, but I've never heard of any.  For commonly used webapps, it just works - and avoids that large, not-so-nice-to-F/LOSS company.

---

