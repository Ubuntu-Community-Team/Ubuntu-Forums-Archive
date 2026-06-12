---
title: "automatically back up mysql database"
date: 2009-04-22
forum: Server Platforms
---

### Post by jeff00z28 on 2009-04-22
I have some databases on mysql that I want to backup to my windows machine automatically at night. Right now im just using phpmyadmins interface or running sql dump commands. I want to export it automatically, then configure a batch script on the windows machine to pull it off the samba share. Any help appreciated.

---

### Post by sonicb00m on 2009-04-22
there's a free linux script called autobackupmysql, i think.

You can dump them locally and use an ftp script to transfer the results. you can also backup remote databases with it.

I run my own batch file that dumps the db then uses scp to transfer the db via sftp.

---

### Post by tornadof3 on 2009-04-22
So look at running the following command on your MySQL machine by using a cron job at your specified time:

```
mysquldump DATABASE -u USERNAME -pPASSWORD > /path/to/samba/share/filename.sql
```

That will put the backup file in your samba share. Then you need to have a batch file that runs on your windows machine to input the data into your backup MySQL machine, eg:

```
mysql DATABASE -u USERNAME -pPASSWORD < N:\path\filename.sql
```

assuming your SAMBA share is mounted as N:\ on your windows machine.

Does that answer your problem?

---

### Post by jeff00z28 on 2009-04-22
> **tornadof3 said:**
> So look at running the following command on your MySQL machine by using a cron job at your specified time:

```
mysquldump DATABASE -u USERNAME -pPASSWORD > /path/to/samba/share/filename.sql
```

That will put the backup file in your samba share. Then you need to have a batch file that runs on your windows machine to input the data into your backup MySQL machine, eg:

```
mysql DATABASE -u USERNAME -pPASSWORD < N:\path\filename.sql
```

assuming your SAMBA share is mounted as N:\ on your windows machine.

Does that answer your problem?

it answers my problem, but the cron isn't working (first time using cron)

i have it set as

# m h  dom mon dow   command
06 16 * * * mysqldump mysql -u root -pbob > /home/bob/Desktop/test.sql

the command works when pasted, but for some reason automating isn't working. thanks!

---

### Post by jeff00z28 on 2009-04-23
nevermind i got it to work. thanks

---

