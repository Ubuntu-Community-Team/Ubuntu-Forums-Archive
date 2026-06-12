---
title: "VsFTP Access Restrictions Help"
date: 2008-05-19
forum: Server Platforms
---

### Post by michaelaly on 2008-05-19
I've setup an encrypted VsFTP server but I'm having trouble restricting access, users have permission to delete files. I have one folder(in /home/FTP-shared) for upload and another for downloading. Inside the download folder I used 
> sudo mount -o bind folder1 downloadFolder
 to make a folder on an external drive(NTFS formatted) accessible for FTP users. I'd like to make the download folder read-only. I'm still learning about Linux, and file and folder permissions still confuse me a bit. I used this tutorial to set this up : [http://ubuntuforums.org/showthread.php?t=518293&highlight=secure+file+transfer](http://ubuntuforums.org/showthread.php?t=518293&highlight=secure+file+transfer). I'm not using virtual users, I have a single 'UserFTP' username setup and users will use this to log into the FTP server. There's no need to have separate usernames for each person. This is all running on Gutsy 32bit Desktop Version. 

Second question : is there a way to view the VsFTP activity in real-time? As in how much bandwidth is being used, how many people are logged in, etc...
thanks.

---

### Post by michaelaly on 2008-05-30
Update : I've attempted using the terminal command chmod to modify the permissions of the download folder to make it read-only. But these permissions don't apply to the NTFS partition which is mounted in the download folder. Any ideas?

---

