---
title: "Automysqlbackup Cron Job Question"
date: 2011-10-19
forum: Server Platforms
---

### Post by fullmoonguru on 2011-10-19
I just installed & configured automysqlbackup and it looks like it's  working fine when I run it manually.  But I'm confused by the script to  put in cron.daily as in the readme file:

```
1. Create a script as below called runmysqlbackup using the lines below:

#~~~~ Copy From Below Here ~~~~
#!/bin/sh

/usr/local/bin/automysqlbackup /etc/automysqlbackup/myserver.conf

chown root.root /var/backup/db* -R
find /var/backup/db* -type f -exec chmod 400 {} \;
find /var/backup/db* -type d -exec chmod 700 {} \;

#~~~~~ Copy To Above Here ~~~~

2. Save it to a suitable location or copy it to your /etc/cron.daily folder.
```

My path is different than /var/backup...  I assume I need to change that  to my path.  Here are my questions:  

1. What is db*?  Can I just list my path all the way to my folder called  automysqlbackups instead?  

2. Why am I chowning & type f'ing etc.  Do I need that?  I assumed  that if the script ran fine manually you would just put a copy in the  cron.daily folder so it would run once a day.

---

### Post by vasile002 on 2011-10-20
db* are the backup file names. The type f&d is what tells the find command to search for files or dirs and the chmod command is to secure the backup files and make them unreadable by anyone.

If you want to run the script daily then you need to either copy it to /etc/cron.daily or you can create a symlink to its current location

---

### Post by fullmoonguru on 2011-10-20
OK, so that's a different script if I want to use it.  I just made a shortcut.  

Thx-

---

### Post by LtPitt on 2011-10-20
Or add it to crontab

sudo crontab -e


0 0 * * * /usr/sbin/automysqlbackup # JOB_ID_1


:)

---

