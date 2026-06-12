---
title: "Ubuntu 16.04 trouble creating Samba share"
date: 2018-05-27
forum: Server Platforms
---

### Post by pclinkcomputers on 2018-05-27
Hello all,

Long-time Windows user, some experience with Mac, new to Linux.  About ready to put my fist through a wall.  I'm wanting to use my Linux machine as a basic file/Plex server.  I've got a small SSD with the OS on it, and a 3TB mechanical drive for all my files.  I've installed Samba, created a user, added the drive through the directory, etc.  I just cannot seem to access the share from my Windows client.  It finally occurred to me to try creating a share from the OS drive, to see if that would work.  It did.  My Windows client was able to open the folder no problem.

So, what's the deal with my second hard drive that's not allowing me to connect?

---

### Post by wildmanne39 on 2018-05-27
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by Morbius1 on 2018-05-28
> I've installed Samba, created a user, added the drive through the  directory, etc.  I just cannot seem to access the share from my Windows  client.  It finally occurred to me to try creating a share from the OS  drive, to see if that would work.  It did.
If you want someone to answer this question based on facts it would be best if you post the output of the following commands so they can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```
If however you would like me to guess it sounds like this second "drive" is mounting to /media/your-user-name/XYZ in which case only the user "your-user-name" will be allowed to reach XYZ. So you can either mount it somewhere else, force all of your users to access the share as "your-user-name", or use the "force user = your-user-name" parameter in the [global] section of /etc/samba/smb.conf.

---

### Post by pclinkcomputers on 2018-05-29
Hello, thank you for replying. Yes, you were correct. I spent some time yesterday fiddling around with it, tried different mounting points, followed a guide on how to configure Samba using the GUI, nothing worked. So I decided to try configuring it with via command line, followed a couple more guides, etc. Still nothing. 

Going back to the GUI, I decided to mess with the drive's permissions. It offered me three different levels: Me, jeremy (which is my user name, but I think it was referring to this second one as a "group"), and then a third category that I believe was called "other." I was kind of afraid to mess with the third one, as I didn't want it opened up to everyone, but ultimately, that's what allowed me to access the drive from my Windows client. So, setting permissions to that third level to read/write fixed it. 

There is one anomaly, though. Any time I've tried to access the share from my Windows client, a dialog pops up asking for credentials. Initially, I expected it to be my Linux user ID and password, but then I read about creating a Samba user and password. So, I created one that mirrored my Linux user ID and password. But that didn't work either. Finally, I tried creating a second Samba user that was totally different than my Linux usernam, and that one works. 

Any thoughts on the credentials issue?

---

