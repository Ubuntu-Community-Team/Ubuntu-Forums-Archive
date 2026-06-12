---
title: "Backup Solutions"
date: 2011-03-15
forum: Server Platforms
---

### Post by david.garceau on 2011-03-15
Not sure if this is the best place for this, but i am currently running two ubuntu servers with approximately 10 tb worth of data. Our ideal goal is to have this data backed up daily offsite. There is about 100gb of data growth per week. BUT there is probably 500gb worth of data being MOVED and or RENAMED. Just wondering if anyone knew of any good methods for this.

---

### Post by david.garceau on 2011-03-15
Even if its a far fetched opinion id love to hear it, I am having a really hard time finding info for something like this.

---

### Post by falko on 2011-03-15
[http://www.howtoforge.com/creating-encrypted-ftp-backups-with-duplicity-and-ftplicity-on-debian-lenny](http://www.howtoforge.com/creating-encrypted-ftp-backups-with-duplicity-and-ftplicity-on-debian-lenny)

For your MySQL databases, you could do something like this: [http://www.howtoforge.com/back_up_mysql_dbs_without_interruptions](http://www.howtoforge.com/back_up_mysql_dbs_without_interruptions)

---

### Post by SeijiSensei on 2011-03-15
I think your first priority is an overall plan.  What needs to be backed up when and where?  What about security over the transfer?  How much history do you need?  How do I avoid backing up stale duplicates?  Etc.

You're probably going to end up writing custom shell scripts that will invoke rsync in various ways. I don't think you'll find off-the-shelf software, either open or proprietary, that can conform to your business needs as well as custom scripting.  Luckily that's the beauty of *nix.  You can make it do almost anything you want.

---

