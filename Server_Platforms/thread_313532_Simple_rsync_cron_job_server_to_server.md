---
title: "Simple rsync cron job server to server?"
date: 2006-12-06
forum: Server Platforms
---

### Post by mhancoc7 on 2006-12-06
I have been searching the web and these forums and have not found a simple way to mirror a directory from one server to another server via a cron job using rsync.

Could someone give me a hand? :)

All I want to do is have a cron job on one of my websites automatically mirror the files from another of my websites.

Thanks in advance!

Jereme

---

### Post by elst on 2006-12-06
If the server holding the master copy has an SSH service then you can run a script on the other server with "rsync -e ssh" to do the sync over an SSH connection. The hardest part is probably setting up user accounts with the right permissions. Where are you getting stuck?

---

### Post by mhancoc7 on 2006-12-06
> **elst said:**
> If the server holding the master copy has an SSH service then you can run a script on the other server with "rsync -e ssh" to do the sync over an SSH connection. The hardest part is probably setting up user accounts with the right permissions. Where are you getting stuck?

I have been reading more and I realize that rsync is not going to work for me since I do not have tghe ability to make those changes on the server that holds the files. Is there a way to use wget with a cron job on the other server to just copy the files automatically?

Thanks so much, Jereme

---

### Post by elst on 2006-12-06
Sure, this just requires you to put the wget command in a script. Cron automatically executes all scripts in the directories /etc/cron.hourly/, /etc/cron.daily/, /etc/cron.weekly/, and /etc/cron.monthly/. To run a script without root access, or for more precise scheduling, use crontab.

My favorite shell scripting tutorial is this one:

[http://www,linuxcommand.org/]("http://www,linuxcommand.org/")

---

