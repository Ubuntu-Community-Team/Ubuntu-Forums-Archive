---
title: "Is this samba file server setup stable enough?"
date: 2009-08-25
forum: Server Platforms
---

### Post by Vunutus on 2009-08-25
I'm setting up a fileserver for work and I just want some more opinions before I tell users that their data is safe when they store it on their network drives.

My abstract goal is to have one public share that all users can access (which is /public on the server), and one private home drive for each individual user.

Here is my smb.conf:

```

[global]
   workgroup = TWINOAKS
   server string = ToR Files
   wins support = yes
   hosts allow = 192.168.1.
   security = user
   dns proxy = no

[homes]
   comment = Home Directories
   browsable = no
   writeable = yes
   valid users = %S

[public]
   comment = Storage (public files)
   path = /public
   public = yes
   writeable = yes

```

I have each XP workstation mapped the following way:
E: = \\myserver\public
P: = \\myserver\homes

It appears to work fine so far. When a user turns on their computer, E: points to the public drive and P: points to their individual home directory. Is there anything I'm missing here or am I good to go? (and yes, I have backups set up for /home and /public)

---

### Post by HermanAB on 2009-08-25
Howdy,

That looks OK to me.  

However, do use rsync and cron.daily to make a nightly backup to another disk drive.

---

