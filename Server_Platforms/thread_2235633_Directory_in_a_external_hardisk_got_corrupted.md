---
title: "Directory in a external hardisk got corrupted"
date: 2014-07-22
forum: Server Platforms
---

### Post by deependra2 on 2014-07-22
hi
   I had mounted an external hardiddk  on a server to transfer some data on it. After the completion of transfer later the hard-disk was accedentally removed without unmounting it from the server. After that when i again plugged in the same hard-disk it was not getting mounted first but after using "fsck" to recover inode values it got mounted. But now when i am using ls command on it, i am getting this output:

[B][root@s-6 exthdd]# ls -l
ls: cannot access pdc_crawler_mongo_backup_1707201: No such file or directory
total 388025536
drwx------. 2 root root        16384 Jul 16 16:30 lost+found
-rw-r--r--. 1 root root 388948397508 Jul 18 23:47 page_crawled_106_36940084-42327225_18072014.sql
-rw-r--r--. 1 root root   9194991765 Jul 10 15:20 pdc_crawler_backup_10072014.tar.bz2
d?????????? ? ?    ?               ?            ? pdc_crawler_mongo_backup_1707201
[/B]
[B]
"pdc_crawler_mongo_backup_1707201"[/B] here is a directory which got corrupted.
cp and mv commands are also not working with this directory. 
It is a 1TB hard-disk with around 700GB data and the size of this corrupted folder is around 330GB.

Plz suggest how to repair/recover this data.

Thanks & Regards,
Deependra Singh

---

### Post by TheFu on 2014-07-22
Use the backup.  Of course, if this is the backup disk, that is problematic.  Perhaps the previous version of the back isn't corrupted and hopefully it isn't more than a day old.  Versioned backups have saved my bacon hundreds of times. A mirror just isn't enough, IMHO.

Other than that, I think you are screwed unless extra steps were taken - perhaps parity files were created to validate the backups?  I do this for media that is really old or for extremely critical data (new baby and wedding photos). par2 is the tool, but it has to be run BEFORE there is any issue.

If the original disk hasn't been touched too much, a professional data recovery company might be able to get most of the data back.  If it is just 1 file, I'd try a few more tools - ddrescue, testdisk, things along those lines - never modifying the original disk of course. All of this needs to happen on another HDD - safely mirrored using a capable that doesn't allow writes back to the source.

Mongo may have data corruption/recovery tools too - I'd ask about those on the mongo-db forums.

I wish you luck. If you get the corrupt file data back, please post the methods used so we can learn too.

---

