---
title: "setting up cron jobs"
date: 2011-07-21
forum: Server Platforms
---

### Post by nimex on 2011-07-21
hello, i'm trying to setup a cron job on my centOS 5.5 server and i was wondering how to go about doing it,

i've read some posts on the "great" interwubz about it and i'm not really sure i understand how to do it correctly.

i've got a job i want to run two times a day, say at 09:00 and 15:00(when i'm not availiable to touch the server physically) it would look something like:
"* 9,15 * * * run-parts /etc/cron.daily/mcbackup"

is it enough that i edit a file and call it mcbackup with the command i want it to do and just put it in the /etc/cron.daily/ folder or do i need to add it to some list somewhere?

also i'm looking for a script to delete the oldest file/folder in for example /home/backups/ only the oldest folder not all of the older ones.

thanks for reading my post.

PS: i am quite noob at this cron stuff so take that into concideration ^^

---

### Post by SeijiSensei on 2011-07-21
run-parts is a special application that cron uses to run applications referenced in the /etc/cron.[hourly|daily|weekly|monthly] directories.  It's not an application that you should use.

The simplest method for adding a cron job is to edit, as root, /etc/crontab.  In your case the entry would look something like:

```
0 9,15 * * * root sh /path/to/your/backup_script
```

That runs the job at 0900 and 1500.

Don't put scripts into the /etc/cron.* directories.  To run a job daily, create the script somewhere else (I use /usr/local/sbin for all my root scripts), then put a symlink to the file in /etc/cron.daily.

As for rotating backups, I create date-coded directories for each day's files, then delete the oldest.  Take a look at [this posting](http://ubuntuforums.org/showpost.php?p=9882114&postcount=5) for ideas.

---

### Post by nimex on 2011-07-21
ty, but how do i make a symlink?
as previously stated, i'm quite noob at this :p

---

### Post by ruffEdgz on 2011-07-21
To make a symlink with this example in mind, you can do it like so:
```

ln -s /path/to/your/backup_script /etc/cron.daily/backup_script

```
First part of the ln -s command is the source/target and the second part is the destination.

You can read more by using the command below:
```

man ln

```
Cheers!

---

### Post by SeijiSensei on 2011-07-21
In your case you don't need to make a link because you don't want the process to run at one of the normally scheduled times.  You need to make a custom entry in /etc/crontab as I wrote above.

---

### Post by nimex on 2011-07-22
so i basically just nano /etc/crontab and add my line to the file then?

edit: the line which runs the scriptfile i mean

---

