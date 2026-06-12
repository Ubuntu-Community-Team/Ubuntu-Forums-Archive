---
title: "Cronjob to syncronize folders"
date: 2009-02-12
forum: Server Platforms
---

### Post by wattaman on 2009-02-12
Can someone write the corect cronjob to syncronize content from, let's say, *path/to/folder1* with *path/to/folder2*. I'm not sure if I'll make myself understood with my English, so I'll say it in other words, too:
- I want the content of *folder1 *to be copied into *folder2*, every night

Also, I'm trying to find a cron to import a table from one database into another table to a different database. The second one already contains some of the first database, so I suppose it should be dropped first... but I'm no expert... that's why I'm asking for the cron :)

Thank you!

---

### Post by punx45 on 2009-02-12
rsync is the tool for synchronizing and backups.   you can set up a cron to have rsync to copy your folder1 to folder2.   

heres something to get started with [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by falconed7 on 2009-02-12
Here is a very good rsync guide for setting up a cronjob to sync/backup at the intervals you want.

[http://www.marksanborn.net/howto/use-rsync-for-daily-weekly-and-full-monthly-backups/](http://www.marksanborn.net/howto/use-rsync-for-daily-weekly-and-full-monthly-backups/)

---

### Post by HermanAB on 2009-02-13
Cron:
It has a limited environment, so always use the full path name for any program in a cron script.

Database:
If you drop a database, it will be deleted!
Don't do that!

[http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html](http://dev.mysql.com/doc/refman/5.1/en/mysqldump.html)

Cheers,

Herman

---

### Post by wattaman on 2009-02-13
Thanks, guys!
I'll try the experiments tonight. Hopefully I'll not bring down the server again :)

---

### Post by wattaman on 2009-02-13
> **wattaman said:**
> Thanks, guys!
I'll try the experiments tonight. Hopefully I'll not bring down the server again :)

K. tested it and doesn't work.
anyway, without Rsync, isn't any cron command to copy and overwrite content from one folder to another ?!
It would be much more simple, don't you think?

---

### Post by punx45 on 2009-02-13
it would work, but rsync is more sophisticated than a simple cp.  synchronization is really the key to it rather than just moving things.   it can be very useful if you are backing up a large amount of data, as it will know to only copy files that have changed, etc.

---

### Post by HermanAB on 2009-02-13
Rsync breaks a large file up into blocks, then calculates cryptographic checksums and compares it with the destination and only copies blocks that changed.  You can therefore use rsync to do backups over the slow internet.

Cheers,

Herman

---

### Post by wattaman on 2009-02-14
I've managed to make it work, in the end.
Now, can anyone help me with the other problem? Syncronizing 2 tables between different databases, on the same server?
Thank you!

---

### Post by punx45 on 2009-02-14
you will probably have better luck starting a new thread on that, mention SQL in the title.

also, check that site that was linked to you earlier, dev.mysql.com   if it is the one i am thinking of they have a very good manual on sql.

---

