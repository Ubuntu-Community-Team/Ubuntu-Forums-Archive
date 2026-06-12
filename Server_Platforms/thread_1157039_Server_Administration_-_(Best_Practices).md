---
title: "Server Administration - (Best Practices)"
date: 2009-05-12
forum: Server Platforms
---

### Post by lmlypfan on 2009-05-12
Where would i find a guide that highlights some "best practices" of server administration? 

I'm running a headless LAMP server (9.04) w/ a RAID5 config.
I've also got ProFTPD, OpenSSH, and NFS installed. 

My goal is for my friends to be able to access the RAID array remotely. I have a 2TB of live music that i would like to share either via FTP or HTTP.  

My questions is: 
Where would the best place be to mount the RAID array?
It's currently mounted at /media/RAID5 , with a Music_Live sub directory. 

I do have sub directories in the RAID array that i don't want to be made public, such as /RAID5/Documents.

Where should the RAID array never be mounted?

---

### Post by Alekz_ on 2009-05-12
Well.. You can mount the "media" where you want!

You have to take care of your files/folders when you publish them!

You said that you don't want to publish the "Documents" dir.. So you grant access only for a specific user (your user) and don't publish it into you FTP Server (or any other service you're running)

I don't think there is a forbiden mounting point for anything.. I usualy mount *ANY* device on /mnt just becouse I like...

---

