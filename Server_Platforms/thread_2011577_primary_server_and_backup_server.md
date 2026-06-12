---
title: "primary server and backup server"
date: 2012-06-27
forum: Server Platforms
---

### Post by slacker360 on 2012-06-27
hi am pretty new to linux but i am trying to setup a ubuntu file server with ubuntu 12.04 server. the server will have one small hdd for the OS and two hdd that are spanned using LVM for data. so far i have managed to set this up and am happy with the results although i am doing it on virtaul machines while i learn what i am doing. 

i would then like to have a backup server that the main server turns on with WOL and then transfers all my files across to then shuts it down again. i have managed to copy the data from my server to my backup server using rsync and was thinking of starting my backup script with cron. 

i would like to know if there is a way of transferring my settings, applications that i setup, and updates across to the backup server so that if my main server breaks for any reason then my backup server can become may main server with everything already setup and ready to go.

i have looked into rsync for this also following this tutorial i found [https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync) 

i have got it to work but i have to exclude the /etc folder and some other bits and pieces which seems not quite wright. i have looked at linux-ha and rsnapshot but am a little lost on what to try next. any advise or things i could look into would be greatly appreciated and sorry for the long post but i thought it would help with any possible answers. 

cheers

---

### Post by howefield on 2012-06-29
Thread moved to "*Server Platforms*" forum.

---

