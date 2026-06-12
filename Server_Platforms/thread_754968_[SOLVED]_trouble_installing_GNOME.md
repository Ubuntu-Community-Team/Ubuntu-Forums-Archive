---
title: "[SOLVED] trouble installing GNOME"
date: 2008-04-14
forum: Server Platforms
---

### Post by thejman on 2008-04-14
Hi. I'm having trouble installing GNOME on Ubuntu server 7.10. I run the following: 

sudo apt-get update
sudo apt-get install ubuntu-desktop

It starts to run, and then asks me for the installation CD:

"Media change: please insert the disc labeled
'Ubuntu-Server 7.10_Gutsy Gibbon_ -Release i386 (20071016)'
in the drive '/cdrom/' and press enter"

I do this and it repeats:

"Media change: please insert the disc labeled
'Ubuntu-Server 7.10_Gutsy Gibbon_ -Release i386 (20071016)'
in the drive '/cdrom/' and press enter"

Over and over again. I have it installed on an old IBM netfinity 5000 and want to get the GUI up to start learning and familiarizing with it. During installation I installed all the server softwares except the DNS server (ie: LAMP, PostgreSQL, Samba, MailServer, OpenSSH, etc...).

Is this part of my problem?

Thanks...

---

### Post by Deathrend on 2008-04-14
You need to disable the CD Repository, the Desktop doesn't come with the Server setup CD.  You could try using a Desktop CD if you're not connected to the internet.

Just do this 

```
sudo nano -w /etc/apt/sources.list 
```

Then edit out 
```
deb cdrom:[Ubuntu-Server ... 
```

Add a # at the start of the line

```
# deb cdrom:[Ubuntu-Server ... 
```

Good Luck :)

---

### Post by aysiu on 2008-04-14
And before you exit Nano, be sure to uncomment out all the other lines that start with *deb*.

In other words, right now your software package manager wants to look on your CD for installation files for software you're trying to install. You're trying to get it to look online instead.

By putting the *#* in front of the CD-ROM source, you're basically saying "Ignore this source," and by taking the *#* away from the online source, you're saying "Use this source instead."

To exit out of Nano, press Control-X, Y, and Enter.

---

### Post by thejman on 2008-04-14
Wow, quick response, thanks!

Yup, that did it. Now I know. 

Thanks a lot!

---

### Post by thejman on 2008-04-14
> **aysiu said:**
> And before you exit Nano, be sure to uncomment out all the other lines that start with *deb*.

In other words, right now your software package manager wants to look on your CD for installation files for software you're trying to install. You're trying to get it to look online instead.

By putting the *#* in front of the CD-ROM source, you're basically saying "Ignore this source," and by taking the *#* away from the online source, you're saying "Use this source instead."

To exit out of Nano, press Control-X, Y, and Enter.

Yeah, I'm familiar with the "commenting" and "uncommenting" of lines and arguments in config files from my MC$E stuff. 

I think I cleared them all (but the CROM source line), but no harm in double checking. 

Thanks, again guys.

---

### Post by Deathrend on 2008-04-14
> **thejman said:**
> Yeah, I'm familiar with the "commenting" and "uncommenting" of lines and arguments in config files from my MC$E stuff. 

I think I cleared them all (but the CROM source line), but no harm in double checking. 

Thanks, again guys.

Glad it worked for you ^^

---

