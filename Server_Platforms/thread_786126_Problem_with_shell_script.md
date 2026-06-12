---
title: "Problem with shell script"
date: 2008-05-07
forum: Server Platforms
---

### Post by henrikmadsen on 2008-05-07
Hi, 
I have created a shell script that copies my web dir files, puts them in a tar file, and then to rotate it, I ask it to delete all files older than three days.
If I run it through ssh, it works fine, but when I schedule it to run through cron, it doesn't delete the old files.

The command I'm using in the shell script to delete the files is


#!/bin/bash

find /mnt/sdc/Serverbackup/tar -type f -mtime +3 -exec rm {} \;


The job is scheduled with my own user, and it works when I run the shell script under my own account manually as well, so I don't think it's a permissions issue...

If anyone can shed some light on this, it would be much appreciated.
Running 7.10 ubuntu server, with KDE installed.

Thanks in advance

---

### Post by cdtech on 2008-05-08
Sounds like a permissions problem to me though. Do the backup files have root or user permissions?

I run all of my scripts through root's cron.

just be aware that the find command also removes all old files in the subdirectories as well, I'm sure your aware of that though. Using the "-maxdepth 0" flag limits the search to the current directory only.

Hope this helps.....

---

### Post by markymarknz on 2008-05-08
I have had issues in the past where I want to run commands with cron and it wouldn't work either, however it would work when run manually.
I fixed my problem by putting some system variables at the top of the crontab -e file.
For me I use these variables:
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

Might fix your problem too.

Mark

---

### Post by henrikmadsen on 2008-05-09
Hi,
thanks for the feedback, and sorry I haven't responded. Thought I'd get an email when there was replies...

The backup files are all owned by user.
I will try adding the parameters mentioned to my cron file, and let you know tomorrow, after the script runs again.

If that still doesn't work, I'll change owner of cron job to root.

/henrik

---

### Post by cdtech on 2008-05-09
> **markymarknz said:**
> I have had issues in the past where I want to run commands with cron and it wouldn't work either, however it would work when run manually.
I fixed my problem by putting some system variables at the top of the crontab -e file.
For me I use these variables:
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

Might fix your problem too.

Mark

Great marky, slipped the old mine that one. :)

---

### Post by henrikmadsen on 2008-05-11
hmm... Adding the variables didn't do the trick... Now I have changed the user it runs under to root. When I kick off the cron job manually, it seems to do the trick. Will wait and see what happens.

But why are the permissions acting up? Job is run under user henrik, the files are owned by user henrik...

Thanks
Henrik

---

