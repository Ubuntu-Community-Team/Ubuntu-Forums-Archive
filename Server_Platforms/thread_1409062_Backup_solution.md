---
title: "Backup solution"
date: 2010-02-17
forum: Server Platforms
---

### Post by XP_2600 on 2010-02-17
Hi all, i am not sure whether i selected the right topic or not, so excuse me, well i am mainly a Windows admin, but i do *NIX administration from time to time, for now i need to use an open source solution for backup windows environment mainly, i spent last days playing with bacula and backupPC, and i then chose backupPC, i built a solution with it seems working not bad, but before i go on deeper, i thought asking geeks here better, my main experience with back was with Vertias/Symantec Backup Exec, what do you recommend as most similar backup solution in Ubuntu offer a close level ( i don't backup to tapes i back to hard disks), also a gui is preferred ,while backupPC do a nice work and i handled its client config file (machine_name.pl), but i still do mistakes sometimes and troubleshooting is annoying, i have to backup files from users machines some of these files are running (like PST files), and i could need to backup a database or something from time to time. so whats your opinion all?

---

### Post by mstjohn1974 on 2010-06-05
I don't know if that will help but I just wrote an article to install backup exec remote agent to your ubuntu server and back it up with a windows backup exec server. have a look if it is something you like to do. look here [www.ubuntuvideocast.com]("http://www.ubuntuvideocast.com")

---

### Post by richardjh on 2010-06-05
I had exactly the same situation as you a few weeks back and I asked on The SysAdmin Network for advice. Most of the guys there are Windows administrators, and the general view seems to be user PCs are not backed up, all important data is to be stored on a server.

This however does not answer the question.

You can [read the thread]("http://www.sysadmin-network.com/forum/topics/backing-up-windows-pcs-on-a"). 


The final result is that I now use BackupPC. I trialled it for two weeks  and I had some issues with getting set up but all minor and I am very  happy with BackupPC.

BackupPC DOES NOT BACKUP LOCKED FILES. When Outlook is open the .pst files cannot be backed up. This is a disaster in an office environment where most users leave OUtlook running all the time they are logged in. There is an easy work around though and I put in the thread a little bit about how to get around the .pst problem. 


I especially like the fact that as it backs up to disk it takes advantage of this and uses pooling to minimise disk usage, also being able to set up users to log in and restore files themselves is a bonus, and equally useful is apart from creating a share on the windows machine, there is no PC software to install.

Also user PCs are on sometimes, off sometimes. BackupPC intelligently backs up. If it has missed a backup because the machine wasn't on when it was scheduled to run at 9:00AM it will try again at 10:00AM.

Later on if you find backups are very large or taking too long you have the option of installing Cygwin+rsync on the PCs and using rsync instead of samba to make things much quicker.

Keep us up to date on how things work out for you. I would be interested if you find better alternatives.

---

