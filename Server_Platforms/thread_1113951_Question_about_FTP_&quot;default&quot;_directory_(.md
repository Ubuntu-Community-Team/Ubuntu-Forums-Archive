---
title: "Question about FTP &quot;default&quot; directory (and some other general things)"
date: 2009-04-02
forum: Server Platforms
---

### Post by thevoicesdoneit on 2009-04-02
Hi,

Please bear with me as I'm new to all this!

I have set up an Ubuntu Server basically with 
SSH 
proftpd
Twonkymedia

I have installed samba but have yet to configure it.

I've also created a software RAID1 array that I "mount" via path /media/raid

I've chmod'd /media/raid to "777" to allow "anything"

What I'd like to do is to force proftpd to use my /media/raid mount instead of putting user data into home directories so that ftp upload data is retained on the RAID at all times. First of all, is that a good idea? 

I added 

"DefaultRoot /media/raid"

to my proftpd config file but when I logged in as a particular user, I sort of expected it to place data in "per user":
/media/raid/<username>/

Is it possible to achieve this?
Also, how do I "add" another user via the command line and how does proftpd know which users are "allowed" to upload/download data?

As a second stage, I'd like to configure samba to allow people to log onto the server and to be able to read the /media/raid data only much in the same way that I've pointed Twonkymedia to it to allow media to be served from it.

As a third state, I'd like to allow _select_ users to have r/w access to the /media/raid via Samba from Linux or Windows XP machines. Can someone provide me with a simple guide to acheive that?

Thanks

---

### Post by nquinnathome1 on 2009-04-03
You need to take a look at the default config file for proftpd; you CAN set it up as you want, however your users' home directories should be set to /media/raid/<username> when you create the new users on the system; proftpd then chroots automatically to the home folder for each user automatically once you set it to do so in the proftpd config

You can set home directories for users using the terminal:

```
useradd -d /media/raid/nameOfUser-m nameOfUser
```

For example.

For samba, I cannot recall, but it may be a similar process; if not, you can manually add entires to smb.conf and specify allowed/disallowed users per share.

---

