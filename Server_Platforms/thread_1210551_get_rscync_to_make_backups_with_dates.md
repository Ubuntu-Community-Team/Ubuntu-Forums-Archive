---
title: "get rscync to make backups with dates"
date: 2009-07-11
forum: Server Platforms
---

### Post by bluethundr on 2009-07-11
hi there,

 how do I get rsync to make backups with dates, similar to the way this command makes tarballs with dates?

tar -czf /var/backups/site-stage/beezag_stage-`date +%Y-%m-%d`.tar.gz /var/stage

thanks!!

---

### Post by gombadi on 2009-07-11
> 
tar -czf /var/backups/site-stage/beezag_stage-`date +%Y-%m-%d`.tar.gz /var/stage


The above command puts all files and directories into one file that can be named what ever you want. rsync on the other hand makes a copy of a directory structure. If you try and add date information to the destination side then it will not be a copy of the source.

What I think you are looking for is something like rdiff-backup. Have a look in the repositories and you may find it does what you are wanting.

---

### Post by HermanAB on 2009-07-11
See Rbackup, Rdiffbackup, Rsnapshot:
[http://rbackup.lescigales.org/](http://rbackup.lescigales.org/)

---

### Post by bluethundr on 2009-07-11
that's good advice.

thanks

this is the command that worked for me

```
stage:/var/backups/site-db# rdiff-backup db::/mysql/dbs_beezag /var/backups/site-db/dbs_beezag
```

however there seems to be a slight difference in size between the db 

```

drwx------ 2 mysql mysql     12288 2009-07-04 12:02 dbs_beezag

```

and the one that is backed up

```

drwx------ 3 mysql mysql 8192 2009-07-04 12:02 dbs_beezag

```

once I understand why the difference in size I will automate with cron.

thanks.

---

### Post by gombadi on 2009-07-12
> 
however there seems to be a slight difference in size between the db 


If you mean the 12288 and 8192 then don't worry. The original directory had a large number of files in it sometime in the past so it was allocated more inodes to store the entries - 12288. If the number of files is reduced the inodes allocated to the directory does not reduce. If you rsync to another location then the new location will only allocate enough inodes to store the directory entries for the CURRENT number of files (8192).

By the way the sizes will never match because rdiff-backup creates a directory at the destination so the destination will always use more disk space.

---

### Post by bluethundr on 2009-07-12
ok, greatly clarified. thank you.

---

