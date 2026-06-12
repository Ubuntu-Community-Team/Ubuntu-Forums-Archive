---
title: "question about cron"
date: 2007-05-01
forum: Server Platforms
---

### Post by tommyvon on 2007-05-01
Hi, im running ubuntu on a server (no gui) and have a few questions about how my cron has been running.  

I have it set to back up the entire drive to a 2nd drive, and it runs weekly.  crontab -l gives me this:

> * 4 * * 0 tar cvpzf /media/backupdrive/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /

It runs fine, but gives me a different file size than if i had ran it myself.  Here is what i get in that directory if i run one myself and let cron do the other.

> -rw-r--r-- 1 root    root  591303436 2007-05-01 14:22 backup_myself.tgz
-rw-r--r-- 1 root    root    6441774 2007-04-29 04:59 backup.tgz

obviously the file size is differnet.  Im wondering what im missing here. 
Also, i couldnt seem to get the character strings to work from the documentation i've read.  Ideally i'd like it to call the file backup-$date.tgz or something like that.

thanks.

---

### Post by gombadi on 2007-05-02
What does the small tar file contain? run this to see -
```
tar -tzf /media/backupdrive/backup.tgz | less
```

May give you a clue as to what is wrong.

* 4 * * * 0 means run the script every minute during the hour 4 on day of the week zero. Possibly the reason the time on the file is 04:59
May want to change that to 18 4 * * * 0 or some other minute of your choice:) 

To add the date make the file -
/media/backupdrive/backup$(date +%Y%m%d).tgz

I have not had much luck with that sort of thing in a crontab so I normally create a script file with the command and call the script from the crontab entry. It is also easier to add features like email the results when the script completes.

---

