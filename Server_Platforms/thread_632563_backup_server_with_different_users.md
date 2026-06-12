---
title: "backup server with different users"
date: 2007-12-05
forum: Server Platforms
---

### Post by hkgonra on 2007-12-05
I currently have a server setup for backups of all users data running xp pro ( don't get me started , it was easy to setup at the time ). 
All of my users are running XP home. 
Each user has their own folder using simple ( no passwords ) file sharing , under a backups folder , that whole folder is backed up weekly and taken offsite , currently it is just under 500gb of data. 
I would like to change to linux and accomplish a couple things. 

1. I want each user to only have access to their own data. 

2. I do not want my users to have to login each time. 

3. I want some users ( 3 ) to be able to have access to all files. 

I plan to use windows synctoy to run the backups and send them to the server. This saves them from backing up ALL the data daily since it will only copy changes and new files. 
I am assuming the best way to do this is to map a drive on the local machine to their respective share folder. 

Can this be accomplished with Ubuntu server. 
I am in over my head considering I am a linux newbie ? 

On a side note I am thinking of setting up another server offsite to sync with the backups server so that the data will not have to be physically carrued offsite. Can linux do this as well, where I won't have to copy 500gb each time but only changes ?

---

### Post by crouton on 2007-12-05
Samba provides Windows filesharing features, so you will be able to accomplish what you want.  This is a pretty common scenario so Googling or reading the Samba docs at the Samba.org website (or even the HOWTOs on the Ubuntu forums or wiki) will help you out.

As for offsite backups, rsync is commonly used to determine what has changed and transmit only those changes.  Again, there's probably a HOWTO out there that will help you get started.

---

### Post by hkgonra on 2007-12-05
Thanks , now I know what to look for.

---

