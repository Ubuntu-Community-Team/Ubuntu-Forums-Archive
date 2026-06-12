---
title: "Sever Data Backup"
date: 2010-10-23
forum: Server Platforms
---

### Post by grimm08 on 2010-10-23
I have just set up a Samba server for my Linux/Windows network at my house, however I running in to a small bump when backing up my data. 

I trying to find an effective way to backup and compress my data.

I have tried the tar command but this took over 5 hours to backup 40GB of data.  Does anyone have a better way to accomplish this in a reasonable amount of time.

Hope this helps, my server has a data drive mounted to my /share directory and my backup drive is mounted to my /backup directory.  Also I would like to compress my data so I don't have a 1:1 ratio.

Thanks you help.
Grimm08

---

### Post by Girya on 2010-10-23
> **grimm08 said:**
> I have just set up a Samba server for my Linux/Windows network at my house, however I running in to a small bump when backing up my data. 

I trying to find an effective way to backup and compress my data.

I have tried the tar command but this took over 5 hours to backup 40GB of data.  Does anyone have a better way to accomplish this in a reasonable amount of time.

Hope this helps, my server has a data drive mounted to my /share directory and my backup drive is mounted to my /backup directory.  Also I would like to compress my data so I don't have a 1:1 ratio.

Thanks you help.
Grimm08

checkout rsync. the first time you do a backup it'll take some time after that it can be configured to backup only the files that change. if you go this way checkout lvm2.
it gives you a very easy way to expand your file system. 

I use backuppc as the frontend to rsync because of its web interface. also it pools data to keep the backup size down. I think backups on my network take about 5 minutes for 60 gb of data on a 100mb/s connection

---

