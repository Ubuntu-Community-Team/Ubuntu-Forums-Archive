---
title: "Backing Up Users etc"
date: 2009-12-10
forum: Server Platforms
---

### Post by Vegan on 2009-12-10
So anyone got a script already written to backup all of the user directories conveniently so I can then move it to another machine each day?

---

### Post by JonRohan on 2009-12-10
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

Basically:

> tar -cvpzf backup.tar.gz /home 

---

### Post by Vegan on 2009-12-12
Can I get a date for the file name, so I have multiple backups?

---

### Post by koenn on 2009-12-12
You can do this with rsync and its --backup and --backup-dir options

example here : [http://www.samba.org/rsync/examples.html](http://www.samba.org/rsync/examples.html) (1st  example)

you'll have a full backup in 'current' and incremental history in $BACKUPDIR. Depending on how you specify the $BACKUPDIR var this kan be 7 weekdays, or 31 days of the month, or whataver the 'date' command can produce.

You'll have to understand how this works before you try a restore : it's not like traditional "latest full, then add incremental" backup but rather a 'snapshot' style backup.

---

### Post by Vegan on 2009-12-12
Wanted something simpler. That is overkill for my needs.

---

### Post by koenn on 2009-12-12
maybe try copy/paste in nautilus ? 
simple, and  fully customizable to your needs

---

