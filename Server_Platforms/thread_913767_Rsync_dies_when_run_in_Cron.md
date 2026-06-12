---
title: "Rsync dies when run in Cron"
date: 2008-09-08
forum: Server Platforms
---

### Post by Desert_Rat on 2008-09-08
We are a small company updating our samba file server to Ubuntu 8.04 Server from Ubuntu 7.04 Server. We back up to a USB drive using rsync running in cron. When run at the command line, rsync works fine but when run as a cron job it dies after copying only about 48MB of our 90GB backup. We had no such problem in 7.04.

The relevant line in /etc/crontab is
0 12    * * *   root    rsync -a --delete /data /media/backup

Can anyone help us?

---

### Post by amac777 on 2008-09-08
I don't know if you got any error messages from cron (check the root mail account to see), but I had a very similar problem of rsync not working after upgarding to 8.04 from 7.04. In my situation, rsync was aborting because it couldn't copy /home/*/.gvfs. I did some googling and looking on these forums and although I'm not exactly clear, the .gvfs directory is something that was added in 8.04 that allows a user to read but not other users including root. So rysnc run as root can't read that directory from each user's home directory.

The solution is to add an exclude line on your rsync command. So, in your case, something like this would probably work:

0 12 * * * root rsync -a --delete --exclude=/home/*/.gvfs /data /media/backup

By the way, I read about this in another thread here:
[http://ubuntuforums.org/showthread.php?p=5545440](http://ubuntuforums.org/showthread.php?p=5545440)

Hope this helps!

EDIT: I just realized that won't fix your problem because your source directory is /data so won't include the /home folder. So your best bet is to check the root email account to see what the cron errors are.

---

### Post by hyper_ch on 2008-09-08
why: root rsync?

---

### Post by Desert_Rat on 2008-09-08
I guess that that is how we set it up when using 7.04 so we did the same in 8.04.

---

### Post by amac777 on 2008-09-08
> **hyper_ch said:**
> why: root rsync?

Ha! I was wondering the same thing and so I've been googling and reading about cron for the last hour. 

Anyway, seems that the original poster is directly editing /etc/crontab so they need to have the root to specify which user to run the task as. From my research, that is not a good way to do it.

Instead, according to this page:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

a better way is to set this up as a system cron task under the root user. So enter it like this:

sudo crontab -e

and then add the following line to the root's crontab:

0 12 * * * rsync -a --delete /data /media/backup

---

### Post by Desert_Rat on 2008-09-08
Thanks - I will try that and post the result.

---

### Post by Desert_Rat on 2008-09-10
We deleted the rsync line in /etc/crontab and used 
sudo crontab -e
to insert the line suggested in amac777 reply.

Unfortunately almost the same result as before but this time it only copied some of the directories and none of the files. Again the same rsync command works fine in the command line!

I can only think it must be some permission problem.

---

### Post by amac777 on 2008-09-11
Ok, I would have been suprised if that had of worked anyway. It was more of a style thing. I didn't have any other ideas at the time.

Anyway, I did a little more reading and have another idea. You might want to check out this thread:

[http://ubuntuforums.org/archive/index.php/t-445156.html](http://ubuntuforums.org/archive/index.php/t-445156.html)

To summarize that thread, it looks like cron uses /bin/sh to run commands, whereas you are probably using /bin/bash, which is the default.

To test if this is the problem, type "sh" to run /bin/sh, and then try your rsync command manually again from that shell. If it fails, then the shell is the problem and you can fix it by putting your rsync command in a script that uses bash instead of sh. 

1. Put the script in root's home like this: sudo nano /root/backup_script

The contents should be:

```
#! /bin/bash
# script for rsync backup
rsync -a --delete /data /media/backup
```

2. Make the script exectuable by: sudo chmod 700 /root/backup_script

3. Run that script from cron at the times you want the backup to be run: sudo crontab -e

```
0 12 * * * /root/backup_script
```

---

