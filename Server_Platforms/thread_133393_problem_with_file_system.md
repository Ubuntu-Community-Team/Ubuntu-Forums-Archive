---
title: "problem with file system"
date: 2006-02-20
forum: Server Platforms
---

### Post by tim01 on 2006-02-20
hi all.
at (ubuntu breezy badge) startup i see this error message : mounting local file systems - failed.and also i use this server for sharing files but i can no longer log 
in through my win xp computer.another problem is i get an error when connecting a usb device.before i did not have any problems at all.please can someone advice this motivated linux newcomer?
thank you

---

### Post by Robgould on 2006-02-20
Ok...one at a time.  
 
You dual boot with windows on your computer and now you can't see you windows partition of that computer?
 
You access a windows share on a remote computer and can not see it?
 
Wich of these is your problem, or is it both?

---

### Post by tim01 on 2006-02-20
thanks 
the problem is when i go to my network places (on workgroups) on my windows computer i see the server (ubuntu) but i can not log on it.

---

### Post by Robgould on 2006-02-22
This link, and the links that are in it, tell you pretty much what I know about sharing remotely between windows and linux.  I don't use the network places thing so I don't know what to tell you there.  I do it by mounting the share with smbfs.  I do it this way so that my files become "part" of my files system.  This makes it easier for programs to access them.  The biggest reason I do this is for my MP3 collection.  If I mount the share, players can see the files as part of my files system and use them in playlists.  Its just easier that way.  Here is the link.   If you are unsure about any of the steps, let me know.
 
[http://www.ubuntuforums.org/showthread.php?t=131561]("http://www.ubuntuforums.org/showthread.php?t=131561")

---

