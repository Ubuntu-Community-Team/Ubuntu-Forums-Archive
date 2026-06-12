---
title: "Backup to dvdrw?"
date: 2007-10-09
forum: Server Platforms
---

### Post by benne on 2007-10-09
Hi there. 

I have a ubuntu server running. And i feel like backing it up woudl be great. 

The server has a dvd+rw drive. I would like to use raided discs but that is too expensive. What i want to do is:

 - Make a scheluled job to copy the dirs i want to backup to one locatiation. 
 - Burn them to a dvdrw. 

I want this to happen daily (e.g. at midnight). And since it is a dvdrw disc it has too erease the old data and write the new data. 

How do i do that?

---

### Post by netlogic on 2007-10-09
1. create a directory for scripts
2. script1: 
mkisofs -r -R -J -l -L -allow-multidot -o /tmp/backup.iso -graft-points "/home/user1=/home/user1" && cdrecord dev=0,4,0 -v --eject speed=4 
3. edit your /etc/crontab
crontab format
# Use the hash sign to prefix a comment
# +---------------- minute (0 - 59)
# |  +------------- hour (0 - 23)
# |  |  +---------- day of month (1 - 31)
# |  |  |  +------- month (1 - 12)
# |  |  |  |  +---- day of week (0 - 7) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  command to be executed

0 *    * * *   root  /home/you/scriptdirectory/script1

---

### Post by benne on 2007-10-09
dev = 0,4,0 <- What IDE device does this mean?

Otherwise, thanks :) 

And how do i set up the cronjob to do this daily. And does this command skip ejecting the writer? And how do i set it up to copy multiple directories?

---

