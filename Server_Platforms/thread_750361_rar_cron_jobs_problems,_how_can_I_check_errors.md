---
title: "rar cron jobs problems, how can I check errors?"
date: 2008-04-09
forum: Server Platforms
---

### Post by peterzog on 2008-04-09
I am running this:

0 0 * * 1 rar a -w/mnt/ /media/se/dmsBackupMon /mnt/dms

I should be getting a large .rar (about 10 gig's) but I only get a 2.3 mb rar


When I run this command manually it works fine.  How can I see what the problem is?  Is there a way to see any errors?  I looked under /var/logs/messages and didn't see anything relevant.  

Any thoughts?

---

### Post by smileypaul on 2008-04-10
Look into the    script   command.. 

man script


you should be able to 

```
script -c 'rar a -w/mnt/ /media/se/dmsBackupMon /mnt/dms'  /var/log/rarlog
```

something like that anyways.

you'll have to create /var/log/rarlog, and make sure you user can write to it.. or put the log somewhere else, home directory, whatever.

That will dump the output of the rar command, make sure you append the  v  switch so the command is verbose.  (otherwise the log file will be empty!)

---

