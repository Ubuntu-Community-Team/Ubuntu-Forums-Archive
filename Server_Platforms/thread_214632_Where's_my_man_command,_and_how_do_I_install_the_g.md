---
title: "Where's my man command, and how do I install the gui"
date: 2006-07-12
forum: Server Platforms
---

### Post by dustparticle on 2006-07-12
Just installed Ubuntu server 6.06. I Tried to use the man command, but I get the following error:

-bash: man: command not found

Also i'm trying to install a gui (ubuntu-desktop), but keep getting:

E: Couldn't find package ubuntu-desktop

This is what I have done so far:

Started Ubuntu Server 6.06
Logged in as root
Inserted Ubuntu Desktop 6.06 CD
At the prompt I typed: "apt-cdrom add"
The command is completed successfully and the CD-ROM is added to /etc/apt/sources.list
I then typed the following commands:
apt-get clean
apt-get update
apt-get install ubuntu-desktop

All the commands are completed successfully except the last one (apt-get install ubuntu-desktop). I just get:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-desktop

Thanks in advance for any help provided.

---

### Post by endfx on 2006-07-13
Try this:

First:
edit the /etc/apt/sources.list.
One of the first lines probably lists the CDROM or CD as a source.
Get rid of that line -- comment it out or delete it.

Next, uncomment all other lines that start with either:
deb
OR
deb-src

Save the file and run:
apt-get update

(as root)

Now run:
apt-get install ubuntu-desktop

(as root, obviously)

This will install everything for a standard desktop box. 

Let me know how it goes.

---

### Post by dustparticle on 2006-07-14
> **endfx said:**
> Try this:

First:
edit the /etc/apt/sources.list.
One of the first lines probably lists the CDROM or CD as a source.
Get rid of that line -- comment it out or delete it.

Next, uncomment all other lines that start with either:
deb
OR
deb-src

Save the file and run:
apt-get update

(as root)

Now run:
apt-get install ubuntu-desktop

(as root, obviously)

This will install everything for a standard desktop box. 

Let me know how it goes.


Something must have gone very wrong during the installation. I found that lots of things were missing (probably because of some issues I had during install with raid). While waiting for a reply to this thread I did a reinstall and then everything worked perfectly. Thank you for your suggestions though, they are much apreciated.

Regards d.

---

### Post by PanzerMKZ on 2006-07-14
well where you able to update to the desktop with everything on the Desktop CD?  no internet connection?



Panzer

---

