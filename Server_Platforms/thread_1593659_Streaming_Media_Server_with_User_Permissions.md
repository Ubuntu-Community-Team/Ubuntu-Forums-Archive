---
title: "Streaming Media Server with User Permissions"
date: 2010-10-11
forum: Server Platforms
---

### Post by feverlax on 2010-10-11
I'm looking to set up a media server (with Ubuntu Server Edition) to stream mostly movies (mkv files at that) across our LAN network, but I have a fairly specific set of goals and requirements for it, and need a little help getting off in the right direction, so I was hoping for a few pointers on how to achieve most of what I want. I want the server to do and be set up as follows:

1. Stream HD (.mkv) and SD (.wma, .avi, etc) movies to clients                  running any type of OS (Windows, Linux or OS X)

2. Be user and password protected. (As of right now I plan on using a SAMBA share with user accounts, but have also read about computer accounts that can be used to restrict access to certain computers as well, which would be nice)

3. Have multiple (2 to start) usergroups. One being the admin group that has read write modify permissions for everything, and another group, mediastreaming, for all the clients of the server so they would only have read permissions. The problem I have come upon during planning is that I want the admins to be in the mediastreaming group as well while maintaining r/w/m. Is this as simple as setting the permissions for the mediastreaming group and then setting them for the admin group? Also, can you set user permissions for groups as a whole or can it only be done for individual users?

4. Have one folder share that includes multiple hdd's. Namely, I want to have one folder called movies, but I want that folder to appear as one to the client even though it will be across multiple disks. Is it possible to do this without RAIDing them together? I was thinking something along the lines of Windows Home Server storage pool. I don't really need data redundancy which (from what I understand) takes away the need for RAID.

I have started looking around on here as well as other Linux sites out there to get started, but I would love if someone were able to point me in the right direction/help with any of these. Furthermore, I have some experience with CLI, and really want to learn it (this server is part learning project, so time is not of the essence) but at the same time, have no objections to using a GUI. Thanks guys (sorry for the long read)

---

### Post by arrrghhh on 2010-10-11
I don't think any streaming server will (mediatomb might...) so you'd probably be better off getting the permissions of the files it's pointing to correct.

Then run the mediaserver as that user, and then it'll only have access to those files.

Although this probably won't work as you'll need multiple media server apps running to achieve this properly...

---

### Post by feverlax on 2010-10-11
Just so I understand, I'd set up a user account for each user on the server (Ubuntu Server) and then set file permissions for them, and then have them run the server account (through Twonky, or whatever it may be) with their user account?

---

### Post by arrrghhh on 2010-10-11
> **feverlax said:**
> Just so I understand, I'd set up a user account for each user on the server (Ubuntu Server) and then set file permissions for them, and then have them run the server account (through Twonky, or whatever it may be) with their user account?

Yes... Although this make not work so well.  I use PS3MediaServer, but only one user... so it's quite simple setup for me.

I'm just thinking about how normally people restrict stuff by user account.

I guess if you can have multiple instances (if they're running under different users it should work) then just fire up an instance under each separate username.  Then each program will only have the permissions that you gave to that user...

---

### Post by feverlax on 2010-10-11
The one thing I should add (I don't know if it makes a difference) is that not everyone will be using Linux. I'm hoping to make it accessible to Windows and OSX machines as well

---

### Post by elglas on 2010-10-11
The easiest way to implement something like this will be using windows file sharing (the open source implementation of this is called samba.) create users using ubuntu, set each user up with a smb password (this may be depreciated but the command was:

 ```
sudo smbpasswd <username>
```

in terms of samba configuration you could use a single share for all users, or give each user to their own home directory. (you can set file / directory masks in your samba configuration to ensure that the proper permissions are set when a samba user adds / modifies a file)

In terms of media streaming servers available, I'd recommend ps3 media server (it works with xboxes as well) and it may very well allow you to run one instance per user, or just add all of the directories to it's media paths.

I hope this helps,

Peter

---

### Post by feverlax on 2010-10-12
Thanks guys, I'm definitely looking into SAMBA shares as they seem the best. 

I have updated the original post with all of my goals for this server in hopes of getting a few more pointers from the community. Thanks

---

### Post by kgatan on 2010-10-13
I have the exact same setup at home. I can recommend using webmin to configure the server.
Webmin is a web-gui with easy setup of users and samba.

I dont know regarding hd pools in linux.

If this is all you need you can also consider freenas which has everthing you need, including hd pools with using zfs. 
It also has support for diffrent types of streaming.

However if you want to add more utilities to the server in future id recommend to go ahead wi ubuntu server instead.

---

