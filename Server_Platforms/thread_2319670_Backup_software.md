---
title: "Backup software"
date: 2016-04-06
forum: Server Platforms
---

### Post by kambiz2 on 2016-04-06
Hi,
I've got installed Ubuntu 14.04.02 lts server on my server, I've got any interface graphic installed, I mean I only use console. I'd like to configure backup via ftp. I've about sbackup software. Does anybody know if I can use this software without have  any desktop installed?
Which software do you suggest me?

Thanks very much

---

### Post by oldfred on 2016-04-06
I thought sbackup was a gui front end for rsync.

But I only have desktop, but use rsync.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 

      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[URL="http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use"]http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use

[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[/URL]

---

### Post by mastablasta on 2016-04-07
you have two options pull and push. both have GUI (or webgui) and CLI interfaces. push might be better if your prefer GUI. if you use this, you can have GUI on desktop (grysnc, Areca, Luckybackup,.... ) and keep only cli on server.

---

